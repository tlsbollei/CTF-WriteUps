```yaml
I made a deal with Hulch Hogan (Hulk Hogan's brother) for a treasure map can you get the treaure for me?
```


### Text file with the following elements : 



```yaml
CMM72222+22
CQC52222+22
CH9J2222+22
9H9M2222+22
8PQ42222+22
9P4G2222+22
8Q572222+22
```




Upon making some research, it`s relatively easy to figure out these are so called "Plus Codes"
```yaml
A Plus Code is a short, alphanumeric location code that represents a specific point on the Earth’s surface.
It’s designed to make sharing and finding locations easier, especially in areas without traditional street addresses.
Plus Codes were developed by Google and are part of the open-source Open Location Code (OLC) system.
```



Using the following Python script, we can translate the Plus Codes to Langtitude and Longtitude coordinates
```
from openlocationcode import openlocationcode as olc

plus_codes = ["CMM72222+22",
              "CQC52222+22",
              "CH9J2222+22",
              "9H9M2222+22",
              "8PQ42222+22",
              "9P4G2222+22",
              "8Q572222+22"
]

for plus_code in plus_codes:
      coordinates = olc.decode(plus_code)
      print(coordinates.latitudeCenter, coordinates.longitudeCenter)
```

Result : 
```
83°00′00.225″N 85°00′00.225″E
78°00′00.225″N 123°00′00.225″E
77°00′00.225″N 52°00′00.225″E
57°00′00.225″N 53°00′00.225″E
45°00′00.225″N 102°00′00.225″E
52°00′00.225″N 110°00′00.225″E
33°00′00.225″N 125°00′00.225″E
```

You can notice here that the first double-digit of every coordinate falls between the ASCII range (0-127)
Therefore we have the decimal numbers in this specific order :
```
83 85 78 123 77 52 57 53 45 102 52 110 33 125
```
Translate from decimal to ASCII :
https://gchq.github.io/CyberChef/#recipe=From_Decimal('Space',false)&input=ODMgODUgNzggMTIzIDc3IDUyIDU3IDUzIDQ1IDEwMiA1MiAxMTAgMzMgMTI1

Therefore we get the flag

```
SUN{M495-f4n!}
```

