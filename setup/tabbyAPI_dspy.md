#=========================
#general
#=========================
create ressources/repos folder

#=========================
#tabbyAPI
#=========================
git clone https://github.com/theroyallab/tabbyAPI

cd tabbyAPI

start.sh

#then need to write something in the configuration file

#name needs to be specified and picked up in the DSPy server access?


#then can start a server which is by default on http://locahost:5000

To obtain your keys, start the API once which will generate a YAML file called api_tokens.yml

#=========================
#DSPy
#=========================
pip install dspy-ai



lm = dspy.{provider_listed_below}(model="your model", model_request_kwargs="...")