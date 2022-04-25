buildctl build --frontend dockerfile.v0 --local context=. --local dockerfile=.

cd /home/jenkins/agent/workspace/buildctl-test
buildctl build --frontend dockerfile.v0 --local context=. --local dockerfile=./buildctl

each repo needs to deploy an image to docker repository a config.json with credentials

create the auth:

echo -n 'admin:admin123jwabcdef' | base64

{
    "auths": {
        "jw-cloud.org:18443": {
        "auth": "YWRtaW46YWRtaW4xMjNqd2FiY2RlZg==",
        "email": "juergen.wewer@gmail.com"
        }
    }
}
