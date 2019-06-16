.PHONY : rerun clean run build

build :
	docker build -t ssh_ubuntu .

run :
	docker run -d --name ssh_ubuntu -p 2222:22 ssh_ubuntu

clean :
	( docker ps -a | grep ssh_ubuntu ) && docker kill ssh_ubuntu || true
	( docker ps -a | grep ssh_ubuntu ) && docker rm ssh_ubuntu || true
	ssh-keygen -f ~/.ssh/known_hosts -R "[localhost]:2222"

rerun : | clean build run