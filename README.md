# Personalized AI Badminton Coach

Advanced analytics for badminton games, using computer vision and gen AI.




## Inspiration

There are over 300 million badminton players looking to improve their game. There’s no way coaches can give personalized insights to so many people!

## How we built it

We use a Flask backend to handle video upload and HTTP requests. Once the client uploads their game footage, we use pretrained models based on [Keypoint RCNN](https://pytorch.org/vision/main/models/keypoint_rcnn.html) for detecting both the players position and the court boundaries. Furthermore, we use a pretrained [TrackNetV3 model](https://github.com/alenzenx/TracknetV3) (published by Kaohswing University) to get pixel coordinates of the birdie on each video frame.

In order to make useful insights on the game, we must map pixel coordinates of the birdie and player to real world coordinates. This is done using projective transformation based on the court boundaries that we previously detected. All of this data is then sent to the client as a json file.

We use Next.js and TailwindCSS to build the frontend, along with heatmap.js for the graphs. We then integrated Anthropic’s Claude 3.5 Sonnet to be our “Birdie Baddie” coach, accessing all of the player’s game data and answering any related questions.
