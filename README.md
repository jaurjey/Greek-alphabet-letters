# Greek Alphabet Classification Model

## What is the model classifying?
The model is classifying **all 24 lowercase Greek alphabet letters**, plus one extra **“no letter”** class.

## What dataset are you using?
We used a dataset created and trained with **Teachable Machine**.  
Each class contained images of lowercase Greek letters in different fonts and styles.  
For the “no letter” class, we included images of walls, people, and backgrounds to help the model distinguish letters from random noise.

## What are the classes in the model?
The model includes **25 classes**:
- 24 lowercase Greek letters:  
  α, β, γ, δ, ε, ζ, η, θ, ι, κ, λ, μ, ν, ξ, ο, π, ρ, σ, τ, υ, φ, χ, ψ, ω  
- 1 extra class: **No letter (background/person/wall)**  

## How many examples per class did you use?
- **25 images per class** (~625 total images).

## What meta-parameters did you use for training?
- **Epochs:** 100  
- **Batch size:** 16  
- **Learning rate:** 0.001  
- **Image size:** Default (224 × 224)  
- **Data augmentation:** *Could not enable horizontal flip in the Teachable Machine online tool; only available in the desktop app.*  

---

# Analysis Questions

### What strategies did you employ to achieve good performance?
- Kept the dataset balanced with exactly 25 images per class.  
- Added a **“no letter” background class** to reduce false positives.  
- Used diverse images (different fonts, colors, and textures).  
- Experimented with learning rate and epochs until accuracy stabilized.  

### Under what circumstances did the model fail? Do you have a hint on why it fails?
- Misclassified letters when they looked **too similar to Latin characters** (e.g., ν vs. v, ο vs. o).  
- Confusion increased with **blurry or low-resolution letters**.  
- Sometimes labeled backgrounds incorrectly if the texture looked like letter strokes.  

### Which classes and class types were difficult to train? How did you overcome the issue?
- **σ (sigma)** was tricky because of its two lowercase forms (σ and ς). We included both forms in the dataset.  
- **ν (nu), ο (omicron), and ρ (rho)** were hard because of overlap with Latin letters. We used more varied fonts.  
- The **“no letter” class** sometimes confused the model, but including multiple types of backgrounds improved results.  

### Was it difficult to achieve good performance while increasing the number of classes? If so, why?
- Yes. With 25 classes and only 25 samples each, the model had little data to distinguish between visually similar letters.  
- Increasing the number of classes made it easier to overfit, so we had to keep the dataset balanced and carefully curated.  

### How robust is your model to changes in the environment?
- Works well across **fonts, backgrounds, and sizes**.  
- Less robust with **handwriting, extreme rotations, or unusual styles**, since those were not well represented.  

### Were you surprised by how well the model learned certain classes?
- Yes, distinct letters like **ξ (xi)**, **ψ (psi)**, and **ω (omega)** performed strongly.  
- The **“no letter” class** also worked better than expected, helping filter out random images.  
