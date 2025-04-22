git clone https://github.com/mitre/caldera.git --recursive
cd caldera
source .venv/bin/activate
pip3 install -r requirements.txt
python3 server.py --insecure --build
