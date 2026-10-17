# Linux Fundamentals — Practice

## 1. Soft Links and Hard Links

```bash
mkdir link-practice
cd link-practice

echo "Hello DevOps" > original.txt

ln -s original.txt softlink.txt
ln original.txt hardlink.txt

ls -li
cat softlink.txt
cat hardlink.txt

rm original.txt
cat hardlink.txt
cat softlink.txt

cd ..
rm -r link-practice
```

## 2. User Management

```bash
sudo adduser devopstest
id devopstest
getent passwd devopstest
ls -ld /home/devopstest

sudo deluser --remove-home devopstest
```

## 3. System Logs Using `journalctl`

```bash
journalctl -n 20
journalctl -b
sudo journalctl -p err
sudo journalctl -u nginx -n 50
sudo journalctl -u nginx -f
```

## 4. Essential Linux Commands

```bash
pwd
ls -la
mkdir test
touch test.txt
echo "Learning Linux" > test.txt
cat test.txt
grep "Linux" test.txt
chmod 644 test.txt
ps aux
df -h
du -sh .
curl -I https://example.com
whoami

rm test.txt
rmdir test
```
