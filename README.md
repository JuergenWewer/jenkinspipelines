buildctl build --frontend dockerfile.v0 --local context=. --local dockerfile=.

cd /home/jenkins/agent/workspace/buildctl-test
buildctl build --frontend dockerfile.v0 --local context=. --local dockerfile=./buildctl