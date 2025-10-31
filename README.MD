This is a repo to just source control the app.yml on the discourse production server.
As of this release we have it all working behind cloudflare+traefik in http mode but have run into a serious bug with Discourse running http:// rather than https:// 

So what we have decided is to get Discourse back to https:// and either self-signed or lets encrypt for Traefik certs and we will attempt to isolate all the Traefik configs under the ve-infra repo.  

The cli below is the manual version of the server ci/cd updates which exist on github and work but I dont necessaril want to autorebuild each time as it takes 10 minutes or so.



sudo rm -rf /mnt/efs/docker-files/ve-discourse
git clone https://github.com/ethosvo/ve-discourse.git /mnt/efs/docker-files/ve-discourse


sudo cp /mnt/efs/docker-files/ve-discourse/containers/app.yml \
         /mnt/efs/docker-files/discourse/containers/app.yml
		 
cd /mnt/efs/docker-files/discourse
sudo ./launcher rebuild app		 