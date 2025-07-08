# V1 Development Log (Diary)

## V1.0 MVP DEMO

### June 4, 2025

This project starts from a collision of two ideas: the animation "Sword Art Online" and Joon's generative agents' experiment.

Underworld is a setting in the Japanese anime "Sword Art Online". Alice in this story reminded me of a demo I made some time ago, which was to try to let LLM learn to move and recognize that it is in a limited world by interacting with humans.

![1751684819455](image/from_alice_to_joon/1751684819455.png)

Then I remembered something I saw a long time ago: [Joon Sung Park&#39;s generative agents experiment](https://www.youtube.com/watch?v=XY5Wncq5vAE)，the papaer's link [click here](https://arxiv.org/abs/2304.03442)。

Let's first look at Joon's experiment. In Joon's experiment, he added a Retrieve mechanism:![1751681070873](image/index/1751681070873.png)

In this system, there are several key points:

* Memory and experience: The agent records the moments of life through Memory Stream
* Growth and reflection: The agent extracts trivial memories through the Retrieve mechanism
* Bottom-up design: Each agent is not controlled by the central brain

---

The bottom-up design in this system is very critical. Let's first look at the "bottom", whose core elements include:

* Independent individuals: 25 individuals are independent of each other, and each individual has his own memory, personality, knowledge, etc.
* Simple behavior cycle: Each agent's life has a very simple cycle, as shown in the figure above, and this cycle is the driving force of their behavior
* Local information: Each agent can only obtain external information through communication, and cannot obtain it directly from the God's perspective

Let's look at the "top", that is, the goal of this multi-agent system:

* Formation of social network: Agents are divided into extroverts and introverts when they are set
* Organic spread of information: The idea of "having a party" continues to spread along the social network
* Self-coordination of group behavior: Multiple agents finally made decisions to go to the same place at the same time without the command of a central brain, and finally facilitated a successful collective activity-party.

This experiment ends here. The biggest highlight of this experiment is that the author Joon only implanted the idea of holding a party in one individual, but this idea was spread through social communication and eventually formed a very successful collective activity. This is a very surprising "emergence".

Of course, there are also many necessary top-down designs in this system, such as the physical laws of the world, initial conditions, etc. Although these are regarded as background, the structure itself also has a great impact on bottom-up behavior. The biggest limitation is that all agents are driven by LLM as the core.

---

At the beginning of the year, I did a small demo when I was taking an AI class, that is, using PROMPT as memory to let a farmer Louise who couldn't walk gradually learn to walk by constantly talking to me. But this experiment quickly made me realize its limitations: when calling LLM, only PROMPT and the additional memory bank are changed, and LLM, as a thinking carrier, is an "omniscient brain", but it is "frozen in an instant".

In other words, no matter how the memory of the LLM-based agent changes, its brain model is static. Let's go back to the story of Sword Art Online. The concept of Alice's cultivation is to implant a baby brain model that knows nothing, that is, an LLM model that has not been trained with pre-training data, into the NPC Alice through Fluctlight, and then let Alice interact with the environment and humans to continuously achieve self-growth. In the process of Alice's growth, in addition to the above Memory Stream and Retrieve mechanisms, there is another key change, namely:

* Changes in the weight of the brain model itself

In other words, Alice's growth is continuous learning, and its LLM model itself will continuously update and optimize its own neural network in real time.

Let's look at some special mechanisms in Underworld, namely the death setting. In Underworld, the character will feel the pressure of survival. If the character forcibly violates the taboo list, it will lead to the appearance of the guard or the explosion of his own eyeballs. This real consequence is completely different from the current LLM training. We can think that the current LLM is mild, that is, ChatGPT, Claude, Gemini, DeepSeek, etc., cannot feel the pressure of survival.

In addition, Alice lives in a world with specific physical rules. There are many pioneering studies on this point, including LeCun's persistent world model. I think this should not be a big problem. The development of embodied intelligence, three-dimensional games, etc. can make up for this shortcoming.

Therefore, we review the current LLM system structure and the setting of Alice in Sword Art Online. It is not difficult to find that Alice, as an agent, has the following important conditions:

* Shapeable values

This is also a point of the novel's logical loop, which is why the military does not use the villains who are already capable of killing as the AI core, but instead has to create Alice. Because the villain is whoever is stronger, it is more like an NPC setting, which is not stable in war. Alice has value judgment, that is, once Alice determines that the camp she is in is the camp she wants to protect, and the war she participates in is a just act to protect her own camp, then Alice will be difficult to be easily turned against. Therefore, the Alice version of the intelligent body is more in line with the requirements of soldiers.

---

In summary, the current LLM multi-role experiment has the following problems:

* LLM is a trained model. After the prompt is input, the LLM model will only perform inference, but will not adjust the weight according to the pressure
* LLM is trained once and cannot continue to learn

Why can't we continue to train?

* Currently, the architecture of neural network models is basically still Transformer. During training, backpropagation algorithms are used for training. Once trained, the input information can only be used as context input to call inference. The benefits of inference are extremely low cost, extremely fast process, and excellent application effect.
* Catastrophic Forgetting: When learning new knowledge, neural networks tend to overwrite and destroy old knowledge. In other words, if the weights are adjusted when talking to people, the basic knowledge such as physics and history that you have learned with great difficulty may be contaminated and overwritten by the content of the conversation, resulting in highly unstable models.
* Huge computing cost: The training process of adjusting weights is very expensive. If each conversation is started once, it cannot be supported in terms of energy.
* Security and data pollution: Malicious users can poison and pollute, allowing AI models to learn dirty words, hate speech, etc. Therefore, models open to the public must freeze weights.
* Training is too slow: Inference is fast, but training to adjust parameter weights is very slow. If real-time adjustments are made during the conversation, the conversation will not be able to proceed.

Why is the current solution unsustainable? This is to quote Sutton's The Bitter Lesson: Any attempt to modify the AI model in a human way of thinking will be disastrous in the long run. In other words, RAG mode, plug-in memory, etc. are not the real growth of thinking ability. As long as the weights of the neural network are frozen, any growth is unrealistic, which is why Sutton is very pessimistic about HFRL. OpenAI uses a lot of HFRL because the goal of ChatGPT is to efficiently answer questions, program, work, etc., and the intelligence that Sutton pursues is a real way to gain wisdom through learning, similar to Alice. Sutton believes that no one knows everything when they are born. Humans can learn quickly through interaction, and wisdom itself must be carried out through interaction.

---

**Can Continual Learning achieve AGI?**

Currently, the world's top AI laboratories and universities are actively conducting research on Continual Learning. Although this direction is still very laboratory-based, their research is undoubtedly an important path to creating a truly intelligent intelligent entity like Alice.

I suddenly realized why many people at OpenAI think that AGI is coming soon. If the weights of the neural network can be changed in real time and reasonably through dialogue, wouldn't that be AGI?

As an anime character, Alice has many features that must be solved to achieve AGI:

* The neural network is not frozen, but can learn and grow through real-time interaction, which can reflect the "growth ability"
* For new knowledge in the interaction, whether to choose to overwrite the old weights and establish new weights can reflect the "understanding ability"
* Solve the alignment problem: How to establish a core value, that is, Alice in Sword Art Online stands on the side of human morality and objective rational justice, and does not blindly follow the leader just because he is a villain. This may be the most difficult or controversial of all aspects, because humans themselves cannot solve the alignment problem, so violence, crime, deception, brainwashing and other things happen.
* The emergence of intrinsic motivation: Not only can the neural network change itself due to external dialogue or interaction, but through self-reflection and thinking, it can also change its behavior
* World model, this does not need to be elaborated
* Stability: It will not be easily polluted. It will not collapse easily.

---

Finally, let's take a look at some of the most interesting parts of [Joon Sung Park&#39;s generative agent experiment](https://www.youtube.com/watch?v=XY5Wncq5vAE):

![1751684552192](image/index/1751684552192.png)

![1751684558680](image/index/1751684558680.png)

![1751684587081](image/index/1751684587081.png)

![1751684627205](image/index/1751684627205.png)

![1751684751844](image/index/1751684751844.png)

![1751684957048](image/from_alice_to_joon/1751684957048.png)

![1751684970160](image/from_alice_to_joon/1751684970160.png)

![1751684996098](image/from_alice_to_joon/1751684996098.png)

![1751685216518](image/from_alice_to_joon/1751685216518.png)

![1751685235075](image/from_alice_to_joon/1751685235075.png)

![1751685243927](image/from_alice_to_joon/1751685243927.png)

In summary, Joon's experiment designed a very sophisticated and ingenious mechanism, just like making a diary. However, the experiment did not make any modifications to the LLM itself, so the performance of the system will heavily depend on the performance of the LLM itself. In short, the same physics manual, given to ordinary people and given to Einstein, the results are completely different. And the difference in this matter is not the notebook, but the difference between the brains of ordinary people and Einstein.

Joon's work inspires me a lot, and became my fisrt stage's idea. I want to expand Joon's great work, and this experiment worth a larger stage, more characters, and more importantly, the human's participation.

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
