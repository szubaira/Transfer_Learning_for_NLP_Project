## **Detection of Insincere Questions on Quora via Transfer Learning with TensorFlow Hub Embedding Models**

### **Project Overview**

This project developed a Natural Language Processing (NLP) solution to identify and filter "insincere" questions on the Quora platform—content that is non-genuine, inflammatory, or intended to spread misinformation. By leveraging **Transfer Learning** through pre-trained text embedding models from **TensorFlow Hub**, I successfully transformed raw text data into high-dimensional vectors for classification. The final model effectively automated the detection of toxic content, providing a scalable alternative to manual moderation.

### **Business Understanding**

The primary stakeholder for this project is Quora’s moderation and safety team. In the social Q&A ecosystem, maintaining a high standard of helpfulness is critical for user retention and advertiser trust. Insincere questions—often characterized by a lack of neutral tone, the promotion of sexual content, or the targeting of specific demographic groups—can degrade the community's quality.

The business problem was to reduce the prevalence of these questions without relying on an unsustainable number of human moderators. By implementing an automated NLP classifier, Quora can protect its community health at scale, ensuring that the platform remains a reliable source of information.

### **Data Understanding**

The analysis utilized the **Quora Insincere Questions Dataset**, which includes hundreds of thousands of questions labeled as either sincere (0) or insincere (1).

* **Data Characteristics:** The dataset is highly imbalanced, as the vast majority of questions on the platform are sincere.
* **Methodology:** I utilized pre-trained embeddings (such as **Universal Sentence Encoder** or **gnews-swivel**) to capture semantic meaning rather than just word frequency.
* **Limitations:** A key challenge was the "nuance" of language; some questions may appear insincere based on keywords but may actually be genuine inquiries depending on the context.
* **Visualization:** **TensorBoard** was integrated during the exploratory and training phases to visualize training progress, validation curves, and the distribution of model weights.
<img width="732" height="483" alt="Screen Shot 2026-02-20 at 23 23 53" src="https://github.com/user-attachments/assets/3b6bcba1-2c98-42f5-988a-33778dc3a91e" />

### **Modeling and Evaluation**

The project implemented a **Transfer Learning** workflow, allowing the model to benefit from the general language knowledge stored in TensorFlow Hub's large-scale pre-trained models.

* **Model Architecture:** The pipeline consisted of an input layer for raw strings, a TensorFlow Hub embedding layer, and several dense, fully connected layers for final binary classification.
* **Optimization:** Dropout layers were included to prevent overfitting on the specific vocabulary of the training set.
* **Evaluation Metrics:** Due to the class imbalance, performance was evaluated using:
* **Precision and Recall:** To ensure insincere questions were captured (high recall) while minimizing the accidental removal of genuine content (high precision).
* **F1-Score:** To find the optimal balance between these two metrics.
* **TensorBoard Integration:** Used to track accuracy and loss metrics in real-time, facilitating rapid hyperparameter tuning.
<img width="983" height="493" alt="Screen Shot 2026-02-20 at 23 24 22" src="https://github.com/user-attachments/assets/2164c84d-8d57-4d51-be0b-63833257e463" />
<img width="979" height="508" alt="Screen Shot 2026-02-20 at 23 24 51" src="https://github.com/user-attachments/assets/421a1e0e-0a62-4b88-b05b-b5b2ee9dbf1c" />

### **Conclusion**

This project proves that Transfer Learning is a powerful tool for specialized text classification tasks where context and intent are more important than individual word counts. The resulting model provides Quora with an automated line of defense against toxic content.

**Future Steps:**

* **Addressing Class Imbalance:** Implement **SMOTE (Synthetic Minority Over-sampling Technique)** or class-weighted loss functions to improve sensitivity to the "insincere" class.
* **Transfer Learning Expansion:** Experiment with transformer-based models like **BERT** or **RoBERTa** via TensorFlow Hub to better capture long-range dependencies in complex question structures.
* **Deployment:** Create a real-time inference API that flags questions for human review immediately upon submission.
