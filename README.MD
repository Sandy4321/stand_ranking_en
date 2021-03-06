# Demo stand. Model: Ranking (English)

## Installation and start
1. Clone the repo and `cd` to project root:
    ```
    git clone https://github.com/deepmipt/stand_ranking_en.git
    cd stand_ranking_en
    ```
2. Create a virtual environment with `Python 3.6`:
    ```
    virtualenv env -p python3.6
    ```
3. Activate the environment:
    ```
    source ./env/bin/activate
    ```
4. Install DeepPavlov:
    1. Clone the repo and `cd` to project root
        ```
        git clone https://github.com/deepmipt/DeepPavlov.git
        cd DeepPavlov
        ```
    2. Install the requirements:
        ```
        python setup.py develop
        ```
    3. Install `spacy` dependencies:
        ```
        pip install http://lnsigo.mipt.ru/export/en_core_web_sm-2.0.0.tar.gz
        python3.6 -m spacy link en_core_web_sm en --force
        ```
    4. Download model components:
        ```
        python3.6 -m deeppavlov.deep download deeppavlov/configs/ranking/insurance_config.json
        ```
    5. Download NLTK data:
    ```
    $ python3
    >>> import nltk
    >>> nltk.download('punkt')
    >>> exit()
    ```
5. Specify model endpoint host (`host`) and port (`port`) in `common_defaults` or corresponding model section of `utils/server_utils/server_config.json`
6. Return to the `stand_ranking_en` dir
7. Specify virtual environment path (if necessary) in `run_en_ranking.sh`
8. Run model:
    ```
    ./run_en_ranking.sh
    ```

## Building and running with Docker:
1. If necessary, build base docker_cuda and docker_deeppavlov images from:

   https://github.com/deepmipt/stand_docker_base
  
2. Clone the repo and `cd` to project root:
    ```
    git clone https://github.com/deepmipt/stand_ranking_en.git
    cd stand_ranking_en
    ```
3. Build Docker image:
   ```
   sudo docker build -t stand/ranking_en .
   ```
4. Run Docker image:
   ```
   sudo docker run -p <host_port>:6009 -v /path/to/host/vol/map/dir:/logs stand/ranking_en
   ```