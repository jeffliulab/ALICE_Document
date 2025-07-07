# V1 Development Log (Diary)

## V1.0 MVP DEMO

### June 5, 2025

Download Godot, create my first Godot project.

Learn how to create a map, how to use tile and tilemap.

![1751911860114](image/V1_Dev_Diary/1751911860114.png){style="display:block; margin:auto; width:800px;"}

### June 6, 2025

Learn how to create conversations.

Use Ollama and download `llama3.1:8b-instruct-q4_K_M` as the demo's inference model.

![1751911866303](image/V1_Dev_Diary/1751911866303.png){style="display:block; margin:auto; width:800px;"}

### June 7, 2025

Create Resident Class and implement two characters as instances.

Test different versions, it can somehow communicate **but the conversation (use json format) is HIGHLY UNSTABLE.** The problem mainly happens in the format of json, I think it might because the llama3.1:8b-instruct-q4_K_M doesn't have enought inference power on json format output.

See test_scripts/V1/test4

![1751911876193](image/V1_Dev_Diary/1751911876193.png){style="display:block; margin:auto; width:500px;"}

Translate in English:

```
Adam (Priest): I’m very pleased to meet you, Ms. Lily. Your artwork is breathtaking, and I believe your talent comes from God. He has given us inspiration and creativity, allowing us to thank Him through our work. Do you think your art could become a means to express faith in and love for Him?

Lily (Painter): While your praise is an honor, I hope you will continue to appreciate my work. The source of art lies in our perception and experience of the world, and I believe that is also one of the gifts God has given us. I will continue to create wholeheartedly, bringing more beauty and inspiration to everyone.

Adam (Priest): Ah, Lily, your art is not only your perception of the world but also one of the gifts God has bestowed upon you. Your creations indeed bring beauty and inspiration to people. I would like to know more about your sources of inspiration and how you integrate them into your work. This brings to mind the doctrinal relationship between art and spiritual uplifting—could you share some insights?

Lily (Painter): Your generosity deeply honors me, Father Adam. I do believe art can bring people spiritual uplift and tranquility, but that is more about people’s perception of beautiful things. My creations are more rooted in observations of life rather than any special source of inspiration. This is a wonderful topic; we should continue exploring it, hoping to find some shared insights so that we may both benefit.

Adam (Priest): Ms. Lily, your words bring me great comfort. I believe everyone’s art has its unique value. Your work not only brings beauty to people but also evokes reflection on spiritual uplift and tranquility. I would very much like to know, do you think your own art could become a means of evangelism, helping us to better understand God’s will?

Lily (Painter): Although I believe everyone’s art has its unique value, I must emphasize that my creations still stem from observations of life, not from some special inspiration. As I mentioned before, I am devoted to capturing the beauty and reality of the world—elements that not only bring people spiritual uplift and tranquility but are also part of understanding God’s will. Through my art, I hope to create a resonance for everyone, allowing them to feel God’s love and wisdom within it. This is my commitment. I will continue to work in this way, striving to make my art not just beautiful but also a meaningful expression.

Adam (Priest): Ms. Lily, your art not only allows people to experience beauty but also represents another aspect of the soul that God has given to humanity. By capturing the truth and beauty of the world, you bring people spiritual uplift and tranquility—this is testimony to God working among us. If I may ask, in your creative process, which experiences or observations do you consider most important to you?
```
