# Batch updating network.cabal

- Downloading

```
% hackage-cli pull-cabal network 
```

- Changing CRLF to LF

```
% for i in *.cabal                   
do                  
dos2unix $i
done
```

- Changing boundary

```
% for i in *.cabal                   
do               
mv $i tmp
sed 's/base >= 3 \&\& < 5/base >= 3 \&\& < 4.17/' tmp > $i
done
```

- Upload testing

```
%  hackage-cli push-cabal --incr-rev *.cabal > LOG
```

- Removing unchanged cabal files to avoid errors according to LOG

- Final uploading

```
%  hackage-cli push-cabal --publish --incr-rev *.cabal
```

