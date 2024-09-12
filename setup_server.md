## Setup server:

```bash
cd
apt-get update
su -
apt-get install sudo -y

# Wait for the user to be created

git clone https://github.com/cyai/xtts-streaming-server
cd xtts-streaming-server
pip install virtualenv
virtualenv env
source env/bin/activate
sudo apt-get update && \
sudo apt-get install --no-install-recommends -y \
    sox libsox-fmt-all curl wget gcc git git-lfs build-essential libaio-dev libsndfile1 ssh ffmpeg vim
cd server
pip install -r requirements.txt
pip install unidic
export NVIDIA_DISABLE_REQUIRE=1
export NUM_THREADS=2
export COQUI_TOS_AGREED=1
uvicorn main:app --host 0.0.0.0 --port 8000
```

## Setup demo:

```bash
cd
cd xtts-streaming-server
source env/bin/activate
pip install -r test/requirements.txt
apt-get install -y ffmpeg
python demo.py
```
