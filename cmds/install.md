# Details
```
<S:> => My HDD/SSD Boot Partition
<W:> => My HDD/SSD Windows Partition
<D:> => My USB Mounted
```

# Partitioning
```
diskpart
list disk
select disk 0
clean
convert mbr
create partition primary size=512
format fs=ntfs label="System" quick
assign letter S
active
create partition primary
format fs=ntfs label="Windows" quick
assign letter W
```

# Install Windows
```
dism /get-imageinfo /imagefile:D:\sources\install.wim
dism /apply-image /imagefile:D:\sources\install.wim /index:1 /applydir:W:\
bcdboot /s S: /f ALL
```
