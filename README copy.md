# SSMC-CI-Madison-5-20-2025

git submodule update --init --recursive

docker build -t slidev-with-plotly .

docker run --name slidev --rm -it --user node -v ${PWD}:/slidev -p 3030:3030 slidev-with-plotly

docker run --name slidev --rm -it     --user root     -v ${PWD}:/slidev     -p 3030:3030     -e NPM_MIRROR="https://registry.npmmirror.com"     tangramor/slidev:latest

docker run --name slidev-with-plotly --rm -it     --user root     -v ${PWD}:/slidev     -p 3030:3030  slidev-with-plotly