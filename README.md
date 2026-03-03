# numpy_scores.ipynb
import numpy as np

# Set seed for reproducibility
np.random.seed(42)

# Generate scores (5 students, 4 subjects)
scores = np.random.randint(50, 101, size=(5, 4))

print("Scores array:\n", scores)

# 3rd student, 2nd subject (index [2,1])
print("\n3rd student, 2nd subject:", scores[2, 1])

# Last 2 students (all subjects)
print("\nLast 2 students:\n", scores[-2:, :])

# First 3 students, subjects 2 and 3 only
print("\nFirst 3 students, subjects 2 & 3:\n", scores[:3, 1:3])



# Column-wise mean (average per subject)
column_means = np.round(scores.mean(axis=0), 2)
print("\nColumn-wise means:", column_means)

# Add curve using broadcasting
curve = np.array([5, 3, 7, 2])
curved_scores = np.clip(scores + curve, 0, 100)

print("\nCurved scores:\n", curved_scores)

# Row-wise max (best subject per student)
row_max = curved_scores.max(axis=1)
print("\nRow-wise max:", row_max)

row_min = curved_scores.min(axis=1, keepdims=True)
row_max = curved_scores.max(axis=1, keepdims=True)

normalized = (curved_scores - row_min) / (row_max - row_min)

print("\nNormalized scores:\n", normalized)
