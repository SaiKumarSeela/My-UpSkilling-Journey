# Today Learning Resources - Day 3

Developed a Face Recognition system using MTCNN (Multi-task Cascaded Convolutional Networks) for face detection and FaceNet for generating face embeddings.

- Revise the Fundamental: https://www.geeksforgeeks.org/introduction-convolution-neural-network/
    - https://medium.com/analytics-vidhya/convolution-padding-stride-and-pooling-in-cnn-13dc1f3ada26
    - OpenCV CheatSheet: https://cheatography.com/thatguyandy27/cheat-sheets/open-cv/pdf/?last=1505666439

- MTCNN: https://medium.com/@iselagradilla94/multi-task-cascaded-convolutional-networks-mtcnn-for-face-detection-and-facial-landmark-alignment-7c21e8007923

![MTCNN.png](Today%20Learning%20Resources%20-%20Day%203%207bd64b09dc2246d2848510d4671f953f/MTCNN.png)

- FaceNet: https://medium.com/analytics-vidhya/introduction-to-facenet-a-unified-embedding-for-face-recognition-and-clustering-dbdac8e6f02

FaceNet takes an image of the person’s face as input and outputs a vector of 128 numbers
which represent the most important features of a face. In machine learning, this vector is
called embedding.

![facenet.jpg](Today%20Learning%20Resources%20-%20Day%203%207bd64b09dc2246d2848510d4671f953f/facenet.jpg)

### Triplet-Loss

- The triplet-loss function use three pictures during evaluations.
    - The anchor is an arbitrary picture (some person).
    - The picture that is positive belong to the same class (same person). The
    picture that is negative belong to various class (different person) from the
    anchor.
    - The triple loss reduces the distance among the anchor and positive picture
    while increasing distance among anchor and negative picture.

![triplet_loss.png](Today%20Learning%20Resources%20-%20Day%203%207bd64b09dc2246d2848510d4671f953f/triplet_loss.png)

- Followed these Videos for the step by step tutorial on implementation:
    - Part1:  https://youtu.be/bG2tNYs7gw8?si=qv4EUWd0ZDq7FLmn
    - Part2: [https://www.youtube.com/watch?v=9niSMx2vxB4&t=514s](https://www.youtube.com/watch?v=9niSMx2vxB4&t=514s)
- My Github code: https://github.com/SaiKumarSeela/face_recognition_project
- Demo of my working code: [https://www.youtube.com/watch?v=b4KdZaNm7Gc](https://www.youtube.com/watch?v=b4KdZaNm7Gc)