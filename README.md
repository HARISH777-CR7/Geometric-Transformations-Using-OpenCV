# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** HARISH K 

### Register No:
212225230094 

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed
```
tx, ty = 100, 50   # shift right by 100 px, down by 50 px
M_translate = np.float32([[1, 0, tx],
                          [0, 1, ty]])
translated = cv2.warpAffine(img, M_translate, (cols, rows))

show([img, translated], ["Original", f"Translated (tx={tx}, ty={ty})"], (10, 5))
```
### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  
```
smaller = cv2.resize(img, None, fx=0.5, fy=0.5, interpolation=cv2.INTER_AREA)
larger  = cv2.resize(img, None, fx=1.5, fy=1.5, interpolation=cv2.INTER_CUBIC)

show([img, smaller, larger],
     ["Original", "Scaled Down (0.5x)", "Scaled Up (1.5x)"])
```

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  
```
# Horizontal shear (x-direction)
M_shear_x = np.float32([[1, 0.5, 0],
                        [0, 1,   0]])
sheared_x = cv2.warpAffine(img, M_shear_x, (int(cols * 1.5), rows))

# Vertical shear (y-direction)
M_shear_y = np.float32([[1,   0, 0],
                        [0.5, 1, 0]])
sheared_y = cv2.warpAffine(img, M_shear_y, (cols, int(rows * 1.5)))

show([img, sheared_x, sheared_y],
     ["Original", "Horizontal Shear", "Vertical Shear"])
```

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  
```
flip_horizontal = cv2.flip(img, 1)    # mirror left-right
flip_vertical   = cv2.flip(img, 0)    # mirror top-bottom
flip_both       = cv2.flip(img, -1)   # both axes

show([img, flip_horizontal, flip_vertical, flip_both],
     ["Original", "Horizontal", "Vertical", "Both Axes"], (18, 5))
```

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed 
```
angle = 45
center = (cols // 2, rows // 2)
M_rotate = cv2.getRotationMatrix2D(center, angle, 1.0)   # (center, angle, scale)
rotated = cv2.warpAffine(img, M_rotate, (cols, rows))

show([img, rotated], ["Original", f"Rotated {angle}°"], (10, 5))
```

---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed
<img width="1022" height="357" alt="Screenshot 2026-10-28 085656" src="https://github.com/user-attachments/assets/e978047c-6bae-4491-a269-b3f7e900a740" />

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  
<img width="1386" height="315" alt="Screenshot 2026-10-28 085704" src="https://github.com/user-attachments/assets/c9dfa28c-7642-4de8-8b2f-5e57fdd8b2af" />

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  
<img width="1402" height="442" alt="Screenshot 2026-10-28 085715" src="https://github.com/user-attachments/assets/c1856af2-177a-46d3-ae4e-9f37fc297a4d" />

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  
<img width="1442" height="243" alt="Screenshot 2026-10-28 085724" src="https://github.com/user-attachments/assets/0e0b425e-3bcf-4890-81b0-2f5c7ab65ca2" />

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  
<img width="1098" height="345" alt="Screenshot 2026-10-28 085731" src="https://github.com/user-attachments/assets/d9672067-a5f3-46bd-aba6-a5af9d0cc335" />

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
