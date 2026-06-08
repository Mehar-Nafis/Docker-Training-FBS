## Bind Mount in Docker

```
mkdir /home/ubuntu/share
```
```
echo 'Hello From Docker Host' > /home/ubuntu/share/index.html
```
```
docker run -d -it --name container3 --mount type=bind,source=/home/ubuntu/share/,target=/app nginx:latest
```
```
docker inspect container3
```
```
docker exec -it container3 bash
```
```
cd app && ls
```
```
cat index.html
```
```
echo "hello from container3" > index.html
```
```
exit
```
```
cd /home/ubuntu/share/
```
```
cat index.html
```

