# Joint-demosaicking-and-zooming-using-moderate-spectral-correlation-and-consistent-edge-map
Implement Joint demosaicking and zooming using moderate spectral correlation and consistent edge map by pf Dengwen Zhou with python


We test the code with Kodak test image

```python=
# read image
img = cv.imread('kodim01.png');
cols,rows,h = img.shape;
zoom = np.zeros([math.floor(cols/2),math.floor(rows/2)]);

#resize image
zoom = img[0:cols-1:2,0:rows-1:2]; 
#get the bayer image
tmp = bayer_reverse(zoom);
#Do the algorithm
out = DZ(tmp);
cv.imwrite('output.bmp',out);

b=12;

#Compare the original image with our output
MSE_R, MSE_G, MSE_B, CPSNR, PSNR_R, PSNR_G, PSNR_B = cpsnr_calc(img,out,b);

print('CPSNR = %lf ' %CPSNR)
```
