#in general, there is the way to use the transformers library by HF to download models


#=========================
#suggested models
#=========================
#cmd r + is huge but like gpt4



#=========================
#template stuff
#=========================

#suggested install github clone
git clone --single-branch --branch 6_5 https://huggingface.co/bartowski/Faro-Yi-9B-200K-exl2 Faro-Yi-9B-200K-exl2-6_5

#suggested install hugginface hub,e.g. faro 9b
pip3 install huggingface-hub
mkdir Faro-Yi-9B-200K-exl2
huggingface-cli download bartowski/Faro-Yi-9B-200K-exl2 --local-dir Faro-Yi-9B-200K-exl2 --local-dir-use-symlinks False
#download from a different branch with revision parameter
mkdir Faro-Yi-9B-200K-exl2-6_5
huggingface-cli download bartowski/Faro-Yi-9B-200K-exl2 --revision 6_5 --local-dir Faro-Yi-9B-200K-exl2-6_5 --local-dir-use-symlinks False


#in general
huggingface-cli download "$model_path" --revision $branch --local-dir /home/user/dev/models/"$model_name" --local-dir-use-symlinks False

#=========================
#downloads
#=========================

model_local_dir="/home/leonard/repos/tabbyAPI/models/"

#=========================
#turboderps exl2 mixtral 8x7b with 6 bpw on both gpu
#=========================

#about 40 min dl time with 35GB size
#dl with 3-5 bpw is only 20 GB

model_path="turboderp/Mixtral-8x7B-instruct-exl2"
model_name="Mixtral-8x7B-instruct-exl2_6bpw"
branch="6.0bpw"
huggingface-cli download "$model_path" --revision $branch --local-dir "$model_local_dir"/"$model_name" --local-dir-use-symlinks False


#=========================
#turboderp/command-r-v01-35B-exl2 with 6 bpw and 16k context both GPU
#=========================

model_local_dir="/home/leonard/repos/tabbyAPI/models/"
model_path="turboderp/command-r-v01-35B-exl2"
model_name="command-r-v01-35B-exl2_6bpw"
branch="6.0bpw"
huggingface-cli download "$model_path" --revision $branch --local-dir "$model_local_dir"/"$model_name" --local-dir-use-symlinks False



#models, sizes, contexts, templates
https://github.com/theroyallab/llm-prompt-templates
holds templates for mixtral and comand-r


Mixtral-8x7B-instruct-exl2_6bpw: 32k max context
command-r-v01-35B-exl2_6bpw, 128k context
mistral 7b 0.1 instruct, maybe has 8k context?
StarCoder2-7B-exl2, has 16k context, template unclear, specialized on github stuff though