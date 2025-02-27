# NLP-SPOC-PROJECT
NLP MODEL FOR TRASLATING ENGLISH INTO FRENCH

Project Overview:
This project focuses on English-to-French translation using a transformer-based model. The implementation leverages Hugging Face's transformers library with the Helsinki-NLP/opus-mt-en-fr model for sequence-to-sequence translation.

Objective:
The primary goal was to train an optimized translation model while ensuring:
•	High translation accuracy using BLEU, ROUGE-L, and METEOR scores.
•	Efficient training by balancing computational cost and performance.
•	Reduction in training time from an estimated 500+ hours to 17 hours through hyperparameter tuning.


Methodology :

1. Dataset Selection & Cleaning
•	Dataset Used: The opus100 dataset (English-French pairs) was chosen for its quality and availability.
•	Initial Data Issues: The raw dataset contained duplicates, null values, and overly long translations.
•	Preprocessing Steps:
o	Filtering duplicates and null values.
o	Removing excessively long translations (>100 words).
o	Final dataset size:
	Training: 32,198 samples
	Validation: 1,109 samples


2. Model Selection & Tokenization
•	Chosen Model: Helsinki-NLP/opus-mt-en-fr, a pre-trained transformer for English-to-French translation.
•	Tokenization:
o	Applied truncation and padding (max length: 128 tokens).
o	Prepared tokenized datasets for efficient processing.


3. Training & Hyperparameter Optimization
Initial Training Setup Issues
•	First training attempt used the following parameters:
o	Learning Rate: 5e-5
o	Batch Size: 32
o	Gradient Accumulation Steps: 1
o	Epochs: 2
o	Warmup Steps: 1000
o	Results: Training time exceeded 500 hours!
Optimized Training Setup
After multiple refinements, the following parameters were used to achieve optimal performance in ~17 hours:
•	Learning Rate: 3e-4 (faster convergence)
•	Batch Size: 16
•	Gradient Accumulation Steps: 2 (for stability)
•	Epochs: 3
•	Warmup Steps: 500
•	Mixed Precision Training (fp16): Enabled to speed up processing.
Final Training Results
•	Final Training Time: ~17 hours (compared to 500+ hours initially)
•	Loss Reduction:
o	Epoch 1: 0.2316
o	Epoch 3: 0.1011


4. Evaluation Metrics
The trained model was evaluated using:
•	BLEU Score: 28.44 (measures n-gram precision)
•	ROUGE-L Score: 0.495 (captures sentence-level recall)
•	METEOR Score: 0.412 (balances precision and recall)
These scores confirm that the model maintains good translation accuracy while significantly reducing training time.

5. Testing & Sample Translations
Example Translations
English Input	French Output
Hello, how are you?	         Comment allez-vous ?
The weather is nice today.	        Le temps est beau aujourd'hui.
I love machine learning!         	J'adore l'apprentissage !
The model demonstrates fluency and accuracy in real-world sentences.

Conclusion
This project successfully optimized English-to-French translation using transformer-based models. By iteratively adjusting hyperparameters, we:
 ✅ Reduced training time from 500+ hours to ~17 hours. 
✅ Maintained high translation quality with BLEU = 28.44, ROUGE-L = 0.495, METEOR = 0.412.
 ✅ Developed an efficient model deployable for real-world translation tasks.
The final trained model is saved as NLP_Project for further testing and fine-tuning.

