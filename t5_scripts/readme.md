The GLUCOSE T5 scripts are plain old T5 scripts, specifying certain parameters. 

To run, first install T5 by following the instructions <a href=https://github.com/ElementalCognition/text-to-text-transfer-transformer>here</a>. Then, make sure all system variables have the right content:


### BOTH SCRIPTS

${T5_ENV} - the path of the python environment for running T5

${TPU_NAME} - the TPU to run on

${PROJECT} - the project name

${ZONE} - the zone of the TPU

(all of the above are required by T5 and described in the T5 documentation)


### DECODING SCRIPT (run_decode_glucose.sh)

${MODEL_DIR} - the path containing the trained GLUCOSE model

${INPUT_FILE} - the file containing data to decode

${OUTPUT_FILE} - the location to output results to


### TRAINING SCRIPT (run_train_glucose.sh)

${T5_DIR} - the path containing the T5 binaries

${DATA_DIR} - the TfdsTask data dir, as described in the T5 documentation

${DATA_FILE} - the file containing the training data

