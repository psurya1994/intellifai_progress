### Things to do:

- voice cloning quality improvements
    - share softvc results, so that paul and jason can make a call. [done]
        - main concern: apr27 is not as great for Jason
	- share the gradio server if they want to run their own training tests. 
- voice cloning misc
    - clean up 1 [done]
        - upload the full model (with vocab.json and config.json) [done]
        - handle the omegaconf environment issue [done]
    - cleanup 2
        - reduce the print statements for xtts train and inference migs. [done]
        - implement minimum and maximum audio limits. [better to be implemented on the front end]
        - implement resemble enhance feature for softvc postprocessing. [done]
    - share the .wav size, always upload .wav files. [done]
    - find minimum audio requirements (is 30 seconds enough?)
        - for both xtts and softvc. run experiments and check.
	- check if we have to build our own datasets, with celebrities.
	- generate 20 mins of audio using xtts, so that they can do a voice translate
- shared server implementation
    - environment setup to support both softvc and xtts [done]
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

Ask Max:
- can we load git with the model tags instead?
