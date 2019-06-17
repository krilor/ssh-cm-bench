.PHONY : rerun clean run build

build :
	docker build -t ssh_ubuntu -f Dockerfile-ubuntu .
	docker build -t ssh_centos -f Dockerfile-centos .

run :
	docker run -d --name ssh_ubuntu -p 2222:22 ssh_ubuntu
	docker run -d --name ssh_centos -p 4444:22 ssh_centos

clean :
	( docker ps -a | grep ssh_ubuntu ) && docker kill ssh_ubuntu || true
	( docker ps -a | grep ssh_ubuntu ) && docker rm ssh_ubuntu || true
	ssh-keygen -f ~/.ssh/known_hosts -R "[localhost]:2222"

	( docker ps -a | grep ssh_centos ) && docker kill ssh_centos || true
	( docker ps -a | grep ssh_centos ) && docker rm ssh_centos || true
	ssh-keygen -f ~/.ssh/known_hosts -R "[localhost]:4444"

rerun : | clean build run