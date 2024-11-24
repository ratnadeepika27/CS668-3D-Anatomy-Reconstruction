# cs668 3d anatomy reconstruction

## Author
Ratna Deepika Pogula

## Affiliation
Pace University

## Email
ratnadeepikapogula@gmail.com

## Project Description
This project aims to automate and improve the reconstruction of missing anatomical structures in medical imaging, forensic research, and 3D bioprinting.

## Abstract 
Reconstructing incomplete 3D anatomical structures is critical for applications in medical imaging, 3D bioprinting, and forensic science. This project explores deep learning models, including 3D GAN, 3D U-Net, and Denoising Autoencoders (DAEs), to automate the completion of missing anatomical structures. By leveraging these models, the work highlights the potential of deep learning to improve efficiency and accuracy in 3D anatomy reconstruction, offering significant advancements for healthcare and scientific applications.

## Research Questions
* How accurately can a deep learning model reconstruct missing 3D anatomical structures?
* Can the model generalize across different types of anatomy (e.g., bones, organs, tissues)?
* What are the optimal deep learning techniques for high-fidelity 3D anatomy completion?

## Dataset
* Dataset Source:
 * The dataset used in this project is derived from the TotalSegmentator collection, designed for comprehensive anatomical
   segmentation in medical imaging. It contains 3D CT images segmented into 104 anatomical structures, including:
   27 organs (e.g., heart, liver, lungs),
   59 bones (e.g., femur, skull, vertebrae),
   10 muscles and 8 vessels.

## Why We Chose These Models:
**3D U-Net:** Known for its encoder-decoder architecture with skip connections, the 3D U-Net is highly effective in preserving spatial details and achieving precise segmentation. It is ideal for accurately reconstructing anatomical structures.

**3D GAN:** GANs excel in generating realistic and visually plausible outputs by learning the underlying distribution of the data. The adversarial training process ensures the generation of high-quality anatomical reconstructions.

**Denoising Autoencoder (DAE):** DAEs are effective at handling noisy or incomplete data by learning robust representations of the input. This makes them suitable for scenarios with corrupted or incomplete input data.

## Methodology
**Data Preparation:**
Preprocessing: The 3D CT scans and their corresponding anatomical segmentations, stored in 'nii.gz' format, are processed using nibabel and NumPy. The data is normalized and visualized to ensure quality.

**Subset Selection:** A subset of 102 subjects is selected to balance data diversity and computational efficiency.

* **Model Implementation:**
3D U-Net: The model utilizes an encoder-decoder structure with 3D convolutions, ReLU activations, and skip connections to preserve spatial details. It is trained with cross-entropy loss, Adam optimizer (learning rate: 0.001), and data augmentation for better generalization.

**DAE:** The DAE employs an encoder-decoder design to denoise and reconstruct missing structures, trained with Mean Squared Error (MSE) loss and Adam optimizer (learning rate: 0.001), using artificially generated noisy data for training.

**3D GAN:** The generator uses 3D transposed convolutions, and the discriminator employs 3D convolutions. The adversarial model is trained with binary cross-entropy loss and alternating updates via Adam optimizer (learning rates: 0.0002 for the generator, 0.0001 for the discriminator).

* **Training and Evaluation:**
 * Training Process: The models are trained on the subset of the dataset, with hyperparameters optimized to handle 3D volumetric
   data. The training uses standard evaluation metrics such as the Dice Coefficient, Fréchet Inception Distance (FID), and
   Inception Score (IS) to assess the quality and realism of the reconstructed anatomical structures.

## Results
The models were trained and evaluated with the following number of epochs:

**3D U-Net:** Trained for 10 epochs, achieving a Dice coefficient of 78.07%, demonstrating strong performance in reconstructing anatomical structures with good spatial detail.

**Denoising Autoencoder (DAE):** Trained for 5 epochs, achieving a Dice coefficient of 77.7%, indicating slightly lower performance than 3D U-Net, but still impressive in segmentation and reconstruction tasks.

**3D GAN:** Trained for 5 epochs and evaluated with the following scores:

Fréchet Inception Distance (FID): 58.4, reflecting the quality of the generated outputs compared to real data.
Inception Score (IS): 4.92, indicating reasonable diversity and realism in the generated anatomical structures.

