# Side-by-Side Accuracy Comparison: Paper Results(https://openaccess.thecvf.com/content/ICCV2025/papers/Xiang_Evidential_Knowledge_Distillation_ICCV_2025_paper.pdf) vs Our Results

## Knowledge Distillation for Efficient Image Classification on CIFAR-100

This project compares different Knowledge Distillation techniques for efficient image classification on the CIFAR-100 dataset. The main goal is to improve the performance of a lightweight student model by transferring knowledge from a larger teacher model.

The teacher model used in this project is **ResNet110**, while the student model is **ResNet20**. The experiments compare standard hard-label training with three distillation methods: **Vanilla Knowledge Distillation (KD)**, **Decoupled Knowledge Distillation (DKD)**, and **Evidential Knowledge Distillation (EKD)**.

## Dataset

The experiments were performed on the CIFAR-100 dataset.

- Total images: 60,000
- Training images: 50,000
- Testing images: 10,000
- Image size: 32 × 32 RGB
- Number of classes: 100

CIFAR-100 is a challenging image classification dataset because it contains 100 fine-grained object classes. This makes it useful for testing how well knowledge transfers from a large teacher model to a smaller student model.

## Models

| Model Type | Architecture | Purpose |
|---|---|---|
| Teacher | ResNet110 | High-capacity model used to guide the student |
| Student | ResNet20 | Lightweight model trained for efficient inference |

## Methods Compared

### 1. Student / Hard Label / CE

The ResNet20 student is trained using standard cross-entropy loss with ground-truth labels only. This is used as the baseline.

### 2. Vanilla Knowledge Distillation

The student learns from both hard labels and softened teacher predictions using KL divergence loss.

### 3. Decoupled Knowledge Distillation

DKD separates knowledge transfer into target-class and non-target-class knowledge. This helps the student learn better class relationships.

### 4. Evidential Knowledge Distillation

EKD transfers both class probability information and uncertainty-aware knowledge from the teacher using evidential learning.

## Side-by-Side Accuracy Comparison

| Method / Test Value | Paper Accuracy (%) | Our Accuracy (%) |
|---|---:|---:|
| Teacher | 74.31 | 73.69 |
| Student / Hard Label / CE | 69.06 | 69.47 |
| KD / Vanilla KD | 70.67 | 71.25 |
| DKD | 71.06 | 71.57 |
| EKD | 71.51 | 71.27 |

## Results Summary

Our experiments show that Knowledge Distillation improves the performance of the ResNet20 student model compared to standard hard-label training.

- The hard-label student baseline achieved **69.47%**, which is slightly higher than the paper baseline of **69.06%**.
- Vanilla KD improved the student model to **71.25%**, outperforming the paper value of **70.67%**.
- DKD achieved the best result in our experiments with **71.57%**, also higher than the paper value of **71.06%**.
- EKD achieved **71.27%**, which is slightly lower than the paper value of **71.51%**, but still better than the hard-label baseline.

## Key Observation

The results confirm that distillation-based training improves lightweight model performance. In our experiments, **DKD performed the best**, while EKD still showed strong improvement over the standard student baseline.

## Visual Results

The project includes visual comparisons for:

- CIFAR-100 test accuracy comparison
- KL divergence comparison
- Temperature vs KD accuracy
- Teacher-student accuracy gap

These figures help show how each distillation method affects student performance and knowledge transfer quality.

## Conclusion

This project demonstrates that Knowledge Distillation is an effective technique for improving compact image classification models. By transferring knowledge from a ResNet110 teacher to a ResNet20 student, the student model achieves better accuracy while remaining lightweight and suitable for deployment on resource-constrained devices.

Among the tested methods, **DKD achieved the best accuracy in our results**, showing that separating target and non-target class knowledge can improve student learning.
