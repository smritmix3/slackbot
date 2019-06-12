# Python version required to run this project is 3.6.8
# List of package and versions requied to run the project
spacy==2.1.1
scikit-learn==0.19.2
numpy==1.16.2
scipy==1.2.1
sklearn-crfsuite==0.3.6
tensorflow==1.9.0
rasa-nlu==0.13.8
rasa-core==0.11.1
rasa-core-sdk==0.11.0
gunicorn==19.9.0
requests==2.18.4

python -m spacy download en_core_web_lg
python -m spacy link en_core_web_lg en


# (1.) Train the nlu model
		''' python nlu_model.py '''
		
		trains NLU Model and saves the model under nlu/default/chatter folder 
		

# (2.) Train the core Model
		## Start the custom action server by running
				''' python -m rasa_core_sdk.endpoint --actions actions '''
				
		## Open a new terminal and train the Rasa Core model by running:
				''' python dialogue_management_model.py  '''
		
		saves the dialogue management model under models/dialogue
				
# (3.) Online training
			'''  python -m rasa_core.train --online -d config/domain.yml -s data/stories.md -o models/dialogue -u models/nlu/default/chatter --epochs 250 --endpoints endpoints.yml  '''
			
			Note-Make sure the custom action server is running
			
# (4.) Talking to bot
			''' python bot.py '''