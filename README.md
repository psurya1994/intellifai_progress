### Things to do:
- [ ] voice cloning quality improvements
	- [ ] make quality improvements [Surya]
	- [ ] share the gradio server if they want to run their own training tests [Surya]
    - [ ] update the db to match Avtar's structure [Surya]
- [ ] shared server implementation
	- [ ] update the db to match Avtar's structure [Surya]
	- [ ] grafana visualization [Avtar]
- [ ] talking head generation
	- [ ] reproduce SyncTalk [Vishnu]
	- [ ] DFL + SyncTalk [Anuj]
- [ ] ComfyUI demos
	- [ ] Background Removal: create the MIG and run more tests [Aishwary]

### Thinking:
- isn't voice cloning already a solved problem? why are we spending so much more time tuning it?
    - share the previous best results and confirm that they are ok.
    - 

### Daily plan:
April 26:
- The main priority of today is to wrap up the voice cloning quality improvements. [done]
    - Share the old and new results of voice cloning and get feedback. 
    - just revert to the feb 1 model. might be the best thing to do. 

April 27:
- Learn to judge the models, as that will help make more rapid iterations. instead of waiting for other's feedback. If I just do this for today, it will be a good enough accomplishment as that will help me for the next two weeks as I'm debugging issues. 
    - what's the most efficient way to do this? validate jason's and moin's findings.  
        - I agree with Jason that apr 24 model is overall dull, compare to the feb 1 models. Why?
            - hypothesis #1: difference in resemble enhance [rejected]
                - test: fix the difference and generate the new results. done, and double checked that they actually are the same. 
            - hypothesis #2: using a shorter length reference audio. [rejected]
                - test: generate the new results with the same length reference audio.
            - hypothesis #3: difference in the model weights, or other optimizations. 
                - this has been validated to be true by looking at the waveforms. The waveforms of our latest model are quite inline with original waveform, but the feb 1 model has a lot of deviation.
            - hypothesis #4: this is coming from the difference in inference protocol.
                - has been confirmed, used the feb1 checkpoint with apr24 and the results are the same.

April 28:
- Listening to models and making judgements. [done]
    - observations: apr27 vs feb 1
        - surya_1: apr27 slighly better in the beginning, but same after
        - surya_2: apr27 has unnecessary inflections.
- We just need to revert to Feb 1 and make it live in the app.
    - clone into the repo and reproduce the results [done]
    - generate the results for this model, and share for review 
        - jason, paul matches exactly - revert successful! yay!
        - share the results for this model with jason. 
    - make this the main model.
- reobserving
    - apr 27 vs feb 1
        - paul_1: apr27 is better in terms of accent
        - paul_2: apr27 is slightly better in terms of accent

- Work on the server implementation 
    - update the db to match Avtar's structure
    - update softvc and xtts to match new codebase structure.

April 29, plan:
- confirm one of the models [done]
- update the softvc and xtts models [done]
    - implement regeneration (30 mins) [done]
    - implement server prioritization (30 mins)
    - implement resemble enhance for softvc (30 mins)
    - finalize the server deployment side of things
    - share gradio demos
- plan for today:
    - implement xtts and 
- train the voices that Paul asked me to train

Things to ask:
- XTTS shared a default list of speakers, for their usecase. Let me know if we want to reuse any of them. Can share gradio demo to try out.
```
'Claribel Dervla', 'Daisy Studious', 'Gracie Wise', 'Tammie Ema', 'Alison Dietlinde', 'Ana Florence', 'Annmarie Nele', 'Asya Anara', 'Brenda Stern', 'Gitta Nikolina', 'Henriette Usha', 'Sofia Hellen', 'Tammy Grit', 'Tanja Adelina', 'Vjollca Johnnie', 'Andrew Chipper', 'Badr Odhiambo', 'Dionisio Schuyler', 'Royston Min', 'Viktor Eka', 'Abrahan Mack', 'Adde Michal', 'Baldur Sanjin', 'Craig Gutsy', 'Damien Black', 'Gilberto Mathias', 'Ilkin Urbano', 'Kazuhiko Atallah', 'Ludvig Milivoj', 'Suad Qasim', 'Torcull Diarmuid', 'Viktor Menelaos', 'Zacharie Aimilios', 'Nova Hogarth', 'Maja Ruoho', 'Uta Obando', 'Lidiya Szekeres', 'Chandra MacFarland', 'Szofi Granger', 'Camilla Holmström', 'Lilya Stainthorpe', 'Zofija Kendrick', 'Narelle Moon', 'Barbora MacLean', 'Alexandra Hisakawa', 'Alma María', 'Rosemary Okafor', 'Ige Behringer', 'Filip Traverse', 'Damjan Chapman', 'Wulf Carlevaro', 'Aaron Dreschner', 'Kumar Dahl', 'Eugenio Mataracı', 'Ferran Simen', 'Xavier Hayasaka', 'Luis Moray', 'Marcos Rudaski'
```
- Trick to reduce model size during inference:
    - precompute speaker and GPT conditional embeddings? and store only a smaller part of the model. 
    - what if we always condition on the exact same speaker?

To mentioned to Paul: 
- voice cloning is not a solved problem, we still do have issues with other accents. 
- training guidance: if the voice quality is already good, don't use the resemble enhance.

- clarification on XTTS
-  
- 


---
### Rough notes

to do:
- finish xtts training and inference implementation [done]
- finalize the best xtts model.
	- implemented resemble_enhance [done]
	- run softvc for all the voices [done]
	- run more comparisions: softvc, resemble enhance, [done]
	- compare with previous results
	- post process the clips through softvc
	- implement the regeneration trick
- decide how to setup the environments for these on the 4090s
- update sql tables based on avtar's recommendations
- implement shared server for softvc and xtts
- deploy softvc and xtts on the 4090 servers so that it can be tested in the app.

- see the worse performing voice, focus on improving it with various hyperparameters
	- understand the training better by understanding which models are trained.
	- see if the model weights can be stored in fp16
	- 

april 25, 26:
- implement SyncTalk. 

noise removal after XTTS is not needed: https://videosoftware.slack.com/archives/C05JY8X19LL/p1707258302118819?thread_ts=1707219417.890879&cid=C05JY8X19LL


Things to