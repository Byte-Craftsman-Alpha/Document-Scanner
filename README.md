### Scan Documents from using CLI

This python script uses [`NAPS2`](https://www.naps2.com/) to scan documents from the scanner and perform action over the scanned file using `PIL`.
```python
import subprocess
import random
from PIL import Image

class scan:
    def __init__(self,path='C:/Users/Public/Documents',filetype='.jpeg', resolution='50'):
        filename = str(random.randint(1000000,999999999999))+filetype
        subprocess.run([r'C:\Program Files\NAPS2\naps2.console','-o',f"{path}{filename}",'--jpegquality',f'{resolution}','--progress'])
        self.image = path+filename
    def crop(self,top='', bottom='', left='', right=''):
        image = Image.open(self.image)
        cropped_image = image.crop((left, top, image.size[0]-right, image.size[1]-bottom))
        cropped_image.save(self.image)


while input('Scan more ')!= '00':
    scan().crop(top=2224, bottom=150, left=95, right=454)
```
