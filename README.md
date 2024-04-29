### Things to do:

- voice cloning quality improvements
    - share softvc results, so that paul and jason can make a call. [done]
        - main concern: apr27 is not as great for Jason
	- share the gradio server if they want to run their own training tests. 
- voice cloning misc
    - clean up
        - upload the full model (with vocab.json and config.json) [done]
        - handle the omegaconf environment issue
        - reduce the print statements for xtts train and inference migs.
        - implement minimum and maximum audio limits
    - find minimum audio requirements (is 30 seconds enough?)
        - for both xtts and softvc. run experiments and check.
    - share the .wav size, always upload .wav files.
	- check if we have to build our own datasets
	- generate 20 mins of audio using xtts, so that they can do a voice translate
- shared server implementation
    - environment setup to support both softvc and xtts 
    - update sql tables based on avtar's recommendations
	- grafana visualization [Avtar]
- gcp implementation for voice cloning
    - implement gcp as dedicated servers for voice cloning
- talking head generation
	- reproduce SyncTalk [Vishnu]
	- DFL + SyncTalk [Anuj]
- ComfyUI demos
	- Background Removal: create the MIG and run more tests [Aishwary]

### Thinking:
- isn't voice cloning already a solved problem? why are we spending so much more time tuning it?
    - share the previous best results and confirm that they are ok.
    - 

### Daily plan:

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