# Soccer-Player-Reidentification
# Approach behind Re-identification in a single feed: 
YOLOv8 (best.pt): The script uses YOLOv8 to detect and track people, providing bounding boxes and temporary track IDs.
ReID Model: The osnet_x1_0 model from torchreid extracts 512-dimensional feature embeddings for each detected person. This model is pre-trained on extensive datasets, suitable for person reidentification.
Feature Matching: For each detected person, the script extracts features and compares them to a database of previous features using cosine similarity. If the similarity exceeds SIMILARITY_THRESHOLD (0.8 - generally used), the person is assigned the same global ID; otherwise, a new global ID is created.
Feature Database: Stores embeddings per track ID, allowing comparison across frames. The global_id_map ensures consistent IDs for reidentified people.
Visualization: Bounding boxes and global IDs are drawn on the frame, and the output is saved as output.mp4.
