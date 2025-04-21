# Human_Activity_Detection
This project aims to determine different types of human activities using only Wi-Fi signals within a domestic household.


Here there are two python codes:

1) Data Preprocessing :

   In this code we are converting the RAW CSI data into the much more filtered version

   CSI Data Shape (Initial): (19997, 30)
   Labels Shape (Initial): (19997, 1)
   Window Size: 20
   Slide Size: 10
   Initial: (19997, 30)
   After sliding window: (1998, 20, 30)
   Flattened to: (1998, 600) ✅
   Label Matrix (yy)
   Initial: (19997, 1)
   After sliding window: (1998, 3) (one-hot encoded) ✅
   Final Answer 𝑥 = 1998 x=1998 Thus, the final dimensions are:
   𝑥 𝑥 xx → (1998, 600)
   𝑦 𝑦 yy → (1998, 3)

2) Building LSTM code:

   Here we create the LSTM model with the environmental parameters:
     learning_rate = 0.0001
     training_epochs = 50
     batch_size = 16
     n_input = 30  # Features per timestep
     n_steps = 20  # Timesteps (600 / 30 features per step)
     n_hidden = 100  # LSTM units
     activities = ["fall", "sitdown", "standup", "walk"]
     n_classes = len(activities) + 1  # Output classes (one-hot encoded, +1 for "noactivity")
     k_folds = 5

3) Inferencing Code:
   
      This code deals with the prediction of activity for each window and if consequently fall occurs 5 times then the activity is "Fall".




There are 3 more branches other than main branch:

1) Training Datasets:
   
    There are 8 csv files:
     a) fall.csv
     b) sitdown.csv
     c) standup.csv
     d) walk.csv
     e) annotation_fall.csv
     f) annotation_sitdown.csv
     g) annotation_standup.csv
     h) annotation_walk.csv
   
2) Testing Datasets:

     There are 3 csv files:
     a) fall.csv
     b) standup.csv
     c) walk.csv
   
3) LSTM Model:

   This contains the .h5 file which is a trained model with accuracy 93.6 %




![sensors-25-00918-g001-min](https://github.com/user-attachments/assets/0aba08cd-5bea-439d-9cd0-d4e44ba260f7)
