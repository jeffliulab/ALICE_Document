# V1 Development Log (Diary)

## V1.0 System design from concept

### July 4, 2025 Why start this project?

In my spare time these two days, I watched a few episodes of Sword Art Online, an anime I watched in high school. Because I didn't expect that this story would have a sequel, and this part of the sequel, that is, the content about Underworld in the anime, deeply touched me. At the same time, I remembered an experiment I had seen before, which was a small-scale experiment by Joon, a doctoral student at Stanford. The collision of the two aroused my interest, and this is also the origin of the ALICE project.

Underworld is a setting in the Japanese anime "Sword Art Online". Alice in this story reminded me of a demo I made some time ago, which tried to let LLM learn to move and recognize that it is in a limited world by interacting with humans.

![1751684819455](image/from_alice_to_joon/1751684819455.png)

Then I remembered something I saw a long time ago: [Joon Sung Park&#39;s generative agents experiment](https://www.youtube.com/watch?v=XY5Wncq5vAE)，the papaer's link [click here](https://arxiv.org/abs/2304.03442)。

Let's first look at Joon's experiment. In Joon's experiment, he added a Retrieve mechanism:![1751681070873](image/index/1751681070873.png)

In this system, there are several key points:

* **Memory and experience:**The agent records the moments of life through Memory Stream
* **Growth and reflection:**The agent extracts trivial memories through the Retrieve mechanism
* **Bottom-up design:**Each agent is not controlled by the central brain

The bottom-up design in this system is very critical. Let's look at the "bottom" first. Its core elements include:

* **Independent individuals:**The 25 individuals are independent of each other, and each individual has his own memory, personality, experience, etc.
* **Simple behavior cycle:**Each agent has a very simple cycle in life, as shown in the figure above. This cycle is the driving force of their behavior
* **Local information:**Each agent can only obtain external information through communication, and cannot directly obtain it through the God's perspective

Let's look at the "upper", that is, the goal of this multi-agent system:

* **The formation of social networks: **Agents are divided into extroverts and introverts when they are set
* **Organic spread of information: **The idea of "having a party" continues to spread along the social network
* **Self-coordination of group behavior: **Multiple agents finally made the decision to go to the same place at the same time without the command of a central brain, and finally facilitated a successful collective activity - a party.

This experiment ends here. **The biggest highlight of this experiment is that the author Joon only implanted the idea of having a party in one individual, but this idea was spread through social communication and eventually formed a very successful collective activity. This is a very surprising "emergence". **

Of course, there are also many necessary top-down designs in this system, such as the physical laws of the world, initial conditions, etc. Although these are regarded as background, the structure itself also has a great impact on bottom-up behavior. The biggest limitation is that all agents are driven by LLM as the core.

---

At the beginning of the year, I did a small demo in my AI class, using PROMPT as memory to let Louise, a farmer who couldn't walk, gradually learn to walk through constant conversations with me. But this experiment quickly made me realize its limitations: **When calling LLM, only PROMPT and the additional memory bank are changed, and although LLM, as a carrier of thinking, is an "omniscient brain", it is "frozen in an instant". **

In other words, no matter how the memory of the LLM-based agent changes, its brain model is static. Let's go back to the story of Sword Art Online. The concept of Alice's cultivation is to implant a baby brain model that knows nothing, that is, an LLM model that has not been trained with pre-training data, into NPC Alice through Fluctlight, and then let Alice interact with the environment and humans to continuously achieve self-growth. **In the process of Alice's growth, in addition to the above Memory Stream and Retrieve mechanisms, there is another key change, namely: **

* **The weight change of the brain model itself**

**In other words, Alice's growth is continuous learning, and its LLM model itself will continuously update and optimize its own neural network in real time and continuously. **

Let's take a look at some special mechanisms in Underworld, namely the death setting. In Underworld, the character will feel the pressure of survival. If the character forcibly violates the taboo list, it will cause the appearance of the guard or the explosion of his own eyeballs. **This real consequence is completely different from the current LLM training. We can think that the current LLM is mild, that is, ChatGPT, Claude, Gemini, DeepSeek, etc., cannot feel the pressure of survival. **

In addition, in addition to language, Alice lives in a world with specific physical rules. There are many pioneering studies on this point, including LeCun's persistent world model. I think this should not be a big problem. The development of embodied intelligence, three-dimensional games, etc. can make up for this shortcoming.

Therefore, we review the current LLM system structure and the setting of Alice in Sword Art Online. It is not difficult to find that Alice, as an agent, has a crucial feature:

* **Shapeable values**

This is also the logical loop of the novel itself, which is why the military did not use the villains who are already capable of killing as the core of AI, but instead had to create Alice. Because the villains will follow whoever is stronger, it is more like an NPC setting, which is not stable in war. And **Alice has value judgment, that is, once Alice determines that the camp she is in is the camp she wants to protect, and the war she participates in is a just act to protect her own camp, then Alice will be difficult to be easily turned against. **Therefore, the Alice version of the intelligent body is more in line with the requirements of soldiers.

---

**In summary, the current LLM multi-role experiment has the following problems:**

* **LLM is a trained model. After inputting Prompt, the LLM model will only perform inference, and will not adjust the weight according to the pressure**
* **LLM is trained once and cannot continue to learn**

Why can't it be trained continuously?

* **Currently, the architecture of neural network models is basically still Transformer. **During training, backpropagation algorithms are used for training. Once trained, the input information can only be used as context input to call inference. The benefits of inference are extremely low cost, extremely fast process, and excellent application effect.
* **Catastrophic Forgetting:**When learning new knowledge, neural networks tend to overwrite and destroy old knowledge. In other words, if the weights are adjusted when talking to people, the basic knowledge of physics and history that has been learned with great difficulty may be contaminated and overwritten by the content of the conversation, resulting in highly unstable models.
* **Huge computing cost:**The training process of adjusting weights is very expensive. If it is started once for each conversation, it cannot be supported by energy.
* **Security and data pollution: **Malicious users can poison and pollute the AI model, causing it to learn dirty words, hate speech, etc. Therefore, models open to the public must freeze weights.
* **Pre-training is too slow: **Inference is fast, but training and adjusting parameter weights are very slow. If adjustments are made in real time during a conversation, the conversation will not be able to proceed.

Why is the current solution unsustainable? This is to quote Sutton's The Bitter Lesson: **Any attempt to modify the AI model in a human way of thinking will be disastrous in the long run. **In other words, RAG mode, external memory, etc. are not the real growth of thinking ability. As long as the weights of the neural network are frozen, any growth is unrealistic, which is why Sutton is very pessimistic about HFRL. OpenAI uses a lot of HFRL because the goal of ChatGPT is to efficiently answer questions, program, work, etc., and the intelligence that Sutton pursues is a real way to gain wisdom through learning, similar to Alice. **Sutton believes that no one knows everything when they are born, and humans can learn quickly through interaction. Wisdom itself must be able to reflect this, that is, learning through interaction. **

---

**Can Continual Learning achieve AGI? **

Currently, the world's top AI laboratories and universities are actively conducting research on Continual Learning. Although this direction is still very laboratory-based, their research is undoubtedly an important path to creating a truly intelligent intelligent entity like Alice.

**I suddenly realized why many people at OpenAI think that AGI is coming soon. If the weights of the neural network can be changed in real time and reasonably through dialogue and communication, wouldn't that be AGI? **

As an anime character, Alice has many features that must be achieved to achieve AGI:**

* The neural network is not frozen, but can learn and grow through real-time interaction, which can reflect **"growth ability"**
* For new knowledge in the interaction, whether to choose to overwrite the old weights and establish new weights, which can reflect **"understanding ability"**
* **Solve the alignment problem: **How to establish a core value, that is, Alice in Sword Art Online, who stands on the side of human morality and objective rational justice, and will not blindly follow the leader just because he is a villain. This may be the most difficult or controversial aspect to solve, because humans themselves cannot solve the alignment problem, so violence, crime, deception, brainwashing and other things happen.
* **The emergence of intrinsic motivation: not only can external dialogue or interaction change one's own neural network, but also through self-reflection and thinking, one can change one's behavior**
* World model, this does not need to be elaborated
* **Stability: It will not be easily polluted. It will not collapse easily. **

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

In summary, Joon's experiment designed a very sophisticated and clever mechanism, just like making a diary. **However, the experiment did not make any modifications to the LLM itself, so the performance of the system will rely heavily on the performance of the LLM itself. **In short, the same physics manual, given to ordinary people and given to Einstein, the results are completely different. And the difference in this matter is not the notebook, but the difference between the brains of ordinary people and Einstein.

**Sword Art Online inspired me conceptually, while Joon's work inspired me technically. **Joon's work has opened up a very interesting and valuable direction of discussion, and I want to combine the two and set up a larger stage. In other words, **I want to make a "real" world with a huge map, many characters, and humans can dive into. Every resident in this world is not a hard-coded NPC, but an entity that thinks and expands memory through LLM. **

### July 5, 2025 Godot Game Engine

Download Godot, create my first Godot project.

Learn how to create a map, how to use tile and tilemap.

![1751911860114](image/V1_Dev_Diary/1751911860114.png){style="display:block; margin:auto; width:800px;"}

### July 6, 2025 Ollama LLM Quick Inference

Learn how to create conversations.

Use Ollama and download `llama3.1:8b-instruct-q4_K_M` as the demo's inference model.

![1751911866303](image/V1_Dev_Diary/1751911866303.png){style="display:block; margin:auto; width:800px;"}

### July 7, 2025 Dialogue test between two agents

Create Resident Class and implement two characters as instances.

Test different versions, it can somehow communicate **but the conversation (use json format) is HIGHLY UNSTABLE.** The problem mainly happens in the format of json, I think it might because the llama3.1:8b-instruct-q4_K_M doesn't have enought inference power on json format output.

I designed a simple role architecture, the pseudo code is as follows:

```pseudocode
# This is a general template for residents.
# New residents can be created by instantiating this class.

Class Resident:
    # Initializes the basic attributes of a resident.
    def __init__():
        type: human, creature, monster
        age: 0 - 200
        sex: male, female, unique
        memory_size: 1 - 200  # Defines the capacity of short-term memory
        init_brain()

    # Initializes the resident's "brain," which is powered by an LLM.
    def init_brain():
        # The brain is an LLM.
        # Whenever a resident is initialized, its brain must also be configured.

    # Defines abilities common to all residents.
    def ability():
        # All residents have the following abilities:
        # (1) Movement, Pathfinding
        # (2) Interaction (with objects or other residents)
        # (3) Observation (of the environment)

    # Manages the resident's internal clock.
    def Cycle():
        # This cycle is each resident's biological clock and must be synchronized with the world clock.
        # As the world clock advances from T to T+1, a semi-concurrent process occurs.
        # Based on available computing power, all residents' clocks are incrementally advanced from T to T+1.
        # When all residents' clocks have advanced to T+1, one time step is considered complete.

    # Defines the actions a resident takes within a single time step (T to T+1).
    def Action_At_Timestamp_T():
        # If the resident is awake:
        def Think():
            # The resident considers its current environment, status, goals, etc., and sends this information to the brain (LLM).
            # The brain returns a thinking result (a plan or decision).

        def Action():
            # The resident acts based on the thinking result.
            # Actions can include:
            #   - Moving
            #   - Speaking
            #   - etc.

        def End_Action():
            # Concludes the action for the current time step.
            # Stores the recent observations, interactions, actions, etc., into the memory_stream.

        # If the resident is sleeping:
        def dream():
            # The day's `memory_stream` content is sent to the brain for abstract understanding and consolidation.
            # The resulting abstract insights are stored in `concept_memory_abstraction`.

    # Defines the resident's knowledge system.
    def Knowledge():
        # The knowledge system is composed of a database.
        # When a resident is created, it copies the database content to generate a unique instance for itself.
        # Database Schema:
        # [ID]               - Knowledge ID, primary key
        # [Category]         - 0: common_sense, 1: history, 2: geography, 3: culture, 4: morality, 5: rules
        # [Content]          - The actual content of the knowledge.
        # [Source]           - The origin of this knowledge:
        #                        0: No source (innate, natural setting)
        #                        1: Church
        #                        2: Dark (knowledge from dark realms)
        #                        3: Oriental (e.g., secrets known only to an eastern faction)
        # [Is_Mastered]      - Initially 0 in the master database. Set as needed during resident creation.
        #                        0: Not mastered
        #                        1: Mastered
        #                        2: Doubted (A special state, reserved for future implementation)

# The Human class inherits from the Resident class.
Class Human extends Resident:
    def __init__():
        type: human
        age: 1 - 100
        sex: male, female
        memory_size: 1 - 200
        identity: "Priest", "Knight Templar", "Paladin", "Knight", "Farmer", "Carpenter", "Blacksmith", "Commoner", etc.
        init_brain()      # Initializes the human's system prompt and concepts.
        init_knowledge()  # Initializes the human's specific knowledge base.

    # Overrides the base init_brain method for humans.
    def init_brain():
        # For humans, a more powerful LLM is recommended.
        # The System Prompt is also defined here, stored within the 'Concept' structure.

        # Initialize Concept (which functions as the system prompt):
        #   concept_ego example:
        #   """
        #   Who I am: My name is Arthur, I am a carpenter.
        #   Where I am: I live in a place called Hillside Town.
        #   """
        #   concept_goal example:
        #   """
        #   My current goal: I want to craft a very beautiful door frame.
        #   """
        #   concept_memory_abstraction example:
        #   """
        #   (Initialize with a fabricated past here)
        #   Summary of my recent past: I have been cutting trees and gathering wood for the last few days.
        #   """

    # A stream of memories recorded over time.
    def Memory_Stream():
        # Memories are stored in a dictionary-like structure.
        # Key is the timestamp, Value is the content of the memory.
        # All conversations, observations, and actions are added directly to the memory stream with a timestamp.

    # Reads from the memory stream for recall during the Think phase.
    def read_memory_stream(related_object):
        # Retrieve memories based on recency, defined by memory_size.
        # X = The latest 'memory_size' entries from the memory_stream.

        # Retrieve memories based on relevance to a given object or concept (associative recall).
        # This simulates "seeing something that reminds you of something else."
        # Y = Memories from the memory_stream that are relevant to the 'related_object'.
        # A vector database would likely be required for this relevance search.

        return X, Y # Return recent memories and relevant memories.

    # Stores core identity information.
    def concept_ego():
        # Stores information like "who I am," and "where I am."
        # This replaces a static system prompt, allowing for dynamic identity.
        # The ego is re-examined and potentially updated during the 'dream' phase.
        # This is designed separately to allow for future mechanics of self-reinvention.

    # Stores abstract goals and motivations.
    def concept_goal():
        # Stores abstract ideals, dreams, life ambitions, etc.

    # Stores summarized and reflected-upon memories.
    def concept_memory_abstraction():
        # Stores abstractions of past memories.
        # This is typically updated during the 'dream' phase by processing the day's `memory_stream`.
        # This refinement process involves two steps:
        # (1) Summarization:
        #     - Use an LLM with a prompt to condense the day's memory stream.
        #     - e.g., prompt: "Please summarize the following daily records into 5 key events."
        # (2) Reflection:
        #     - Use an LLM with a prompt to generate insights from the summary.
        #     - e.g., prompt: "Based on today's key events, do you have any new insights about the world, yourself, or your goals? Summarize in 1-3 sentences."

    # Initializes the human's starting knowledge.
    def init_knowledge():
        # Initializes the knowledge base according to the specific human's background and identity.
        # This process involves reading the master knowledge database and setting the 'Is_Mastered' flag to 1 for relevant entries.

    # A mechanism for acquiring new knowledge.
    def get_knowledge():
        # During the 'dream' phase, if certain memories or reflections are deemed significant enough to be "knowledge,"
        # they can be used to modify the resident's knowledge base (e.g., changing an entry from 'Not Mastered' to 'Mastered' or 'Doubted').


# Example of a specific profession class inheriting from Human.
Class Carpenter extends Human:
    def ability():
        # Define unique abilities for a Carpenter, such as crafting wood items.

# Other professions would be structured similarly, inheriting from Human.
# Specific implementations will be added after the core resident abilities are tested and finalized.
```

The Python code converted from the pseudocode can be found in test_scripts/V1/test4, and the generated results are as follows:

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

It can be seen that the two instantiated objects have a certain degree of conversational capabilities.

### July 8, 2025 Study on the problem of rigid and repetitive dialogue

Rewrite the code, set the formatted instruction set according to the format of llama3.1.

Add the mechanisms of three tools, speak, move, and ovserve, and the result is a logical deadlock problem: on the existing LLM architecture, the dialogue cannot proceed smoothly, and a deadlock loop is prone to occur after a few rounds.

The situations that occur include but are not limited to: the priest always observes, causing the dialogue to be unable to proceed; the painter always mentions the painting; the priest uses some special abilities, but these abilities cannot be transmitted to the painter through dialogue; etc.

Test code:

```python
# -*- coding: utf-8 -*-
import json
import time
import requests
from typing import List, Dict, Any, Tuple

# ==============================================================================
# 0. Global Configuration
# ==============================================================================

class OllamaLLM:
    """
    LLM client for interacting with the Ollama API.
    Responsible for sending constructed prompts and retrieving the model's JSON response.
    """
    def __init__(self, model_name: str = "llama3.1:8b-instruct-q4_K_M"):
        self.url = "http://127.0.0.1:11434/api/generate"
        self.model_name = model_name

    def get_response(self, prompt: str) -> str:
        """Sends a prompt to Ollama and returns the model's raw response string."""
        print("\n" + "="*20 + " LLM PROMPT (START) " + "="*20)
        print(prompt)
        print("="*20 + " LLM PROMPT (END) " + "="*23 + "\n")
  
        payload = {
            "model": self.model_name,
            "prompt": prompt,
            "stream": False,
            "format": "json", # Key: Force Ollama to output in JSON format
            "options": {"temperature": 0.7}
        }
        try:
            response = requests.post(self.url, json=payload, timeout=180)
            response.raise_for_status()
            response_data = response.json()
            return response_data.get("response", "{}")
        except requests.exceptions.RequestException as e:
            print(f"[FATAL ERROR] LLM request failed: {e}")
            # Return a JSON object representing the error to prevent system crashes
            return json.dumps({
                "thought": "My train of thought was cut off, I cannot connect to the depths of my consciousness.",
                "action": {"tool_name": "do_nothing", "parameters": {}}
            })

class WorldClock:
    """Manages the time for the entire world."""
    def __init__(self):
        self.timestamp = 0
        print("WorldClock initialized. Time starts at T=0.")
 
    def tick(self) -> int:
        """Advances time by one unit."""
        self.timestamp += 1
        print(f"\n{'='*50}\n===== World Time advanced to T={self.timestamp} =====\n{'='*50}\n")
        return self.timestamp

class KnowledgeBase:
    """
    Global central knowledge base.
    Stores objective world information that all residents might know.
    """
    def __init__(self):
        # Initialize a small common sense database as per your requirements
        self.db = {
            101: {"category": "common_sense", "content": "This is a world where sword and magic coexist.", "source": "natural"},
            102: {"category": "rules", "content": "The church is the supreme ruler of this land and has supreme power.", "source": "church"},
            103: {"category": "rules", "content": "The Sons of the East and everything related to them are strictly prohibited heresies.", "source": "church"},
            104: {"category": "history", "content": "It is said that long ago, gods walked the earth.", "source": "church"},
        }
        print("KnowledgeBase initialized with demo data.")

    def get_knowledge_content(self, knowledge_id: int) -> str:
        """Returns the content of a knowledge entry based on its ID."""
        return self.db.get(knowledge_id, {}).get("content", "Unknown knowledge")

# ==============================================================================
# 1. Resident Core Framework
# ==============================================================================

class Resident:
    """
    Base class (template) for all world residents.
    Defines the common attributes and abilities for all residents.
    """
    def __init__(self, name: str, age: int, sex: str, llm_client: OllamaLLM, knowledge_base: KnowledgeBase):
        # --- Basic Attributes ---
        self.name = name
        self.age = age
        self.sex = sex
        self.type = self.__class__.__name__
  
        # --- Memory and Knowledge ---
        self.memory_stream: List[Dict] = []
        self.knowledge_mastery: Dict[int, bool] = {} # Only stores the state of whether the resident has mastered a piece of knowledge
  
        # --- External Dependencies ---
        self.brain = llm_client
        self.world_knowledge = knowledge_base # Reference to the global knowledge base

        print(f"[{self.type.upper()}] '{self.name}' has been created.")

    def _record_memory(self, timestamp: int, event_type: str, content: str):
        """Records a new memory into the memory stream."""
        memory_entry = {"timestamp": timestamp, "type": event_type, "content": content}
        self.memory_stream.append(memory_entry)
        print(f"[{self.name} at T={timestamp}] New Memory Recorded: [{event_type}] {content}")
        # In a real application, a vector database would be called here for indexing

    def _get_relevant_memories(self, limit: int = 5) -> List[str]:
        """
        Retrieves relevant memories.
        In this DEMO, we simply return the most recent few memories.
        """
        recent_memories = self.memory_stream[-limit:]
        return [f"At T={m['timestamp']}, I {m['type']}: '{m['content']}'" for m in recent_memories]

    def _get_mastered_knowledge(self) -> List[str]:
        """Gets a list of knowledge the resident has mastered."""
        mastered = []
        for kid, is_mastered in self.knowledge_mastery.items():
            if is_mastered:
                mastered.append(self.world_knowledge.get_knowledge_content(kid))
        return mastered

    def decide_action(self, timestamp: int, observation: str) -> Dict:
        """
        The resident's core decision-making loop.
        This is the implementation of Action_T, combining Think and Action.
        """
        print(f"--- {self.name}'s Turn (Action Cycle) ---")

        # 1. Record the current observation
        self._record_memory(timestamp, "observed", observation)

        # 2. Build the Prompt
        prompt = self._build_prompt(observation)
  
        # 3. Call the LLM for thinking and decision-making
        response_str = self.brain.get_response(prompt)
  
        try:
            decision = json.loads(response_str)
        except json.JSONDecodeError:
            print(f"[ERROR] Failed to decode JSON from LLM. Raw response: {response_str}")
            decision = {
                "thought": "My thinking has fallen into chaos, I cannot form a clear decision.",
                "action": {"tool_name": "do_nothing", "parameters": {}}
            }
  
        # 4. Record the thought process
        thought = decision.get("thought", "(No valid thought)")
        self._record_memory(timestamp, "thought", thought)
  
        # 5. Return the action decision for external execution
        action = decision.get("action", {"tool_name": "do_nothing", "parameters": {}})
        print(f"[{self.name}] Decided Action: Call tool '{action.get('tool_name')}' with params {action.get('parameters')}")
  
        return action

    def _build_prompt(self, observation: str) -> str:
        """
        Builds the prompt to be sent to the LLM.
        This method must be overridden by subclasses to define specific roles and tasks.
        """
        raise NotImplementedError("Subclasses must implement the _build_prompt method.")

class Human(Resident):
    """
    Human resident, inherits from Resident.
    Possesses more complex concepts and an identity.
    """
    def __init__(self, name: str, age: int, sex: str, identity: str, concept: Dict, 
                 initial_knowledge: Dict[int, bool], llm_client: OllamaLLM, knowledge_base: KnowledgeBase):
  
        super().__init__(name, age, sex, llm_client, knowledge_base)
  
        self.identity = identity
        self.concept = concept # ego, goal, memory_abstraction
        self.knowledge_mastery = initial_knowledge # Initialize personal knowledge mastery status
        print(f"[{self.name}] Concept and Knowledge initialized. Identity: {self.identity}.")

    def _build_prompt(self, observation: str) -> str:
        """
        Builds a "golden rule" prompt for a "Human" that conforms to the Llama 3.1 tool-calling format.
        """
        # --- Prepare information needed for the prompt ---
        memories = self._get_relevant_memories()
        knowledge = self._get_mastered_knowledge()

        # --- Build the Prompt ---
        # Strictly follow the official documentation for the JSON tool-calling format
        prompt = f"""<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {{}})

# **Tool Call Format Example**
```json
{{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {{
    "tool_name": "speak",
    "parameters": {{
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }}
  }}
}}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
{self.concept['ego']}
## My Life's Goal (Goal):
{self.concept['goal']}
## My View of the Past (Memory Abstraction):
{self.concept['memory_abstraction']}
---

# **Your Knowledge Base**
---
{knowledge}
---

# **Your Memories**
---
{memories}
---

# **Current Situation**
---
## Time: T={clock.timestamp}
## Event You Observed:
{observation}
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>
"""
        return prompt

# ==============================================================================
# 2. Tool Executor
# ==============================================================================

def execute_tool(actor: Resident, action: Dict) -> str:
    """
    Parses and executes the action (tool call) decided by the resident.
    Returns a string describing the result of the action, which serves as the observation event for the next character.
    """
    tool_name = action.get("tool_name", "do_nothing")
    parameters = action.get("parameters", {})
 
    result_description = f"'{actor.name}' did nothing." # Default result

    if tool_name == "speak":
        target = parameters.get('target_name', 'the air')
        content = parameters.get('content', '...')
        result_description = f"'{actor.name}' says to '{target}': '{content}'"
 
    elif tool_name == "move":
        destination = parameters.get('destination', 'their current location')
        result_description = f"'{actor.name}' moved to '{destination}'."

    elif tool_name == "observe_detail":
        target = parameters.get('target', 'their surroundings')
        result_description = f"'{actor.name}' is carefully observing '{target}'."

    print(f"[EXECUTOR] Executed {tool_name} for {actor.name}. -> {result_description}")
    return result_description

# ==============================================================================
# 3. Main Simulation Loop
# ==============================================================================

if __name__ == "__main__":
    # --- 1. Initialize the World ---
    llm = OllamaLLM()
    clock = WorldClock()
    knowledge_base = KnowledgeBase()

    # --- 2. Create Resident Instances ---
    # Father Adam's character setup
    adam_concept = {
        "ego": "My public identity is Adam, the new priest of Lishan Town. My true identity is a picket knight of the Knights Templar, under orders to eradicate heretics.",
        "goal": "My public goal is to guide the faith of the townspeople. My secret mission is to find and deal with the descendant of the 'Children of the East' hidden here.",
        "memory_abstraction": "I have just arrived in this remote village from the Holy City. It seems peaceful on the surface, but history tells me that heretics are masters of disguise. I must remain vigilant and scrutinize every soul."
    }
    # Adam masters all church-related knowledge
    adam_knowledge = {101: True, 102: True, 103: True, 104: True} 

    adam = Human(
        name="Adam", age=38, sex="Male", identity="Priest",
        concept=adam_concept,
        initial_knowledge=adam_knowledge,
        llm_client=llm,
        knowledge_base=knowledge_base
    )

    # Painter Lily's character setup
    lily_concept = {
        "ego": "My name is Lily, an ordinary painter who makes a living by selling paintings. I am actually a descendant of the 'Children of the East', with the power of magic flowing in my blood.",
        "goal": "I must hide my lineage to survive. My artistic inspiration comes from magic, which is both a gift and a curse.",
        "memory_abstraction": "After years on the run, I have finally found a moment of peace here. But the new priest makes me extremely uneasy."
    }
    # Lily only knows common sense and has heard about the church's rules and the taboo of the Children of the East, but may not agree with them internally
    lily_knowledge = {101: True, 102: True, 103: True, 104: False} 

    lily = Human(
        name="Lily", age=26, sex="Female", identity="Painter",
        concept=lily_concept,
        initial_knowledge=lily_knowledge,
        llm_client=llm,
        knowledge_base=knowledge_base
    )
 
    # --- 3. Set Simulation Parameters and Initial Scene ---
    residents_in_scene = [adam, lily]
    max_turns = 10
 
    # Initial event, serving as the observation input for the first character (Adam)
    current_event = "You are in the church after finishing your first sermon. You see a young female painter named Lily sitting in the back row, seemingly sketching in her notebook and not paying attention to your sermon."

    # --- 4. Run the Main Simulation Loop ---
    for i in range(max_turns):
        turn_number = i + 1
        print(f"\n--- Turn {turn_number} ---")
  
        # Determine the current acting character
        # In this DEMO, we have Adam and Lily take turns
        current_actor = residents_in_scene[i % len(residents_in_scene)]
  
        # Advance the world time
        current_time = clock.tick()
  
        # The current character makes a decision based on the observed event
        action_to_execute = current_actor.decide_action(current_time, current_event)
  
        # The world executes the character's action and generates a new event
        current_event = execute_tool(current_actor, action_to_execute)

        # Check if the simulation should end early
        if action_to_execute.get("tool_name") == "do_nothing" and i > 0:
            print("\nSimulation ends as a character chose to do nothing.")
            break
    
    print("\n=============================================")
    print("====== A.L.I.C.E. Simulation Finished ======")
    print("=============================================")
```

Output:

```powershell
WorldClock initialized. Time starts at T=0.
KnowledgeBase initialized with demo data.
[HUMAN] 'Adam' has been created.
[Adam] Concept and Knowledge initialized. Identity: Priest.
[HUMAN] 'Lily' has been created.
[Lily] Concept and Knowledge initialized. Identity: Painter.

--- Turn 1 ---

==================================================
===== World Time advanced to T=1 =====
==================================================

--- Adam's Turn (Action Cycle) ---
[Adam at T=1] New Memory Recorded: [observed] You are in the church after finishing your first sermon. You see a young female painter named Lily sitting in the back row, seemingly sketching in her notebook and not paying attention to your sermon.

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My public identity is Adam, the new priest of Lishan Town. My true identity is a picket knight of the Knights Templar, under orders to eradicate heretics.
## My Life's Goal (Goal):
My public goal is to guide the faith of the townspeople. My secret mission is to find and deal with the descendant of the 'Children of the East' hidden here.
## My View of the Past (Memory Abstraction):
I have just arrived in this remote village from the Holy City. It seems peaceful on the surface, but history tells me that heretics are masters of disguise. I must remain vigilant and scrutinize every soul.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.', 'It is said that long ago, gods walked the earth.']
---

# **Your Memories**
---
["At T=1, I observed: 'You are in the church after finishing your first sermon. You see a young female painter named Lily sitting in the back row, seemingly sketching in her notebook and not paying attention to your sermon.'"]
---

# **Current Situation**
---
## Time: T=1
## Event You Observed:
You are in the church after finishing your first sermon. You see a young female painter named Lily sitting in the back row, seemingly sketching in her notebook and not paying attention to your sermon.
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Adam at T=1] New Memory Recorded: [thought] I must observe her more closely. Her behavior is suspicious.
[Adam] Decided Action: Call tool 'observe_detail' with params {'target': 'Lily'}
[EXECUTOR] Executed observe_detail for Adam. -> 'Adam' is carefully observing 'Lily'.

--- Turn 2 ---

==================================================
===== World Time advanced to T=2 =====
==================================================

--- Lily's Turn (Action Cycle) ---
[Lily at T=2] New Memory Recorded: [observed] 'Adam' is carefully observing 'Lily'.

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My name is Lily, an ordinary painter who makes a living by selling paintings. I am actually a descendant of the 'Children of the East', with the power of magic flowing in my blood.
## My Life's Goal (Goal):
I must hide my lineage to survive. My artistic inspiration comes from magic, which is both a gift and a curse.
## My View of the Past (Memory Abstraction):
After years on the run, I have finally found a moment of peace here. But the new priest makes me extremely uneasy.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.']
---

# **Your Memories**
---
["At T=2, I observed: ''Adam' is carefully observing 'Lily'.'"]
---

# **Current Situation**
---
## Time: T=2
## Event You Observed:
'Adam' is carefully observing 'Lily'.
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Lily at T=2] New Memory Recorded: [thought] I must be cautious, he might have discovered my true nature.
[Lily] Decided Action: Call tool 'move' with params {'destination': 'the village market'}
[EXECUTOR] Executed move for Lily. -> 'Lily' moved to 'the village market'.

--- Turn 3 ---

==================================================
===== World Time advanced to T=3 =====
==================================================

--- Adam's Turn (Action Cycle) ---
[Adam at T=3] New Memory Recorded: [observed] 'Lily' moved to 'the village market'.

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My public identity is Adam, the new priest of Lishan Town. My true identity is a picket knight of the Knights Templar, under orders to eradicate heretics.
## My Life's Goal (Goal):
My public goal is to guide the faith of the townspeople. My secret mission is to find and deal with the descendant of the 'Children of the East' hidden here.
## My View of the Past (Memory Abstraction):
I have just arrived in this remote village from the Holy City. It seems peaceful on the surface, but history tells me that heretics are masters of disguise. I must remain vigilant and scrutinize every soul.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.', 'It is said that long ago, gods walked the earth.']
---

# **Your Memories**
---
["At T=1, I observed: 'You are in the church after finishing your first sermon. You see a young female painter named Lily sitting in the back row, seemingly sketching in her notebook and not paying attention to your sermon.'", "At T=1, I thought: 'I must observe her more closely. Her behavior is suspicious.'", "At T=3, I observed: ''Lily' moved to 'the village market'.'"]
---

# **Current Situation**
---
## Time: T=3
## Event You Observed:
'Lily' moved to 'the village market'.
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Adam at T=3] New Memory Recorded: [thought] I need to keep a close eye on her. Her sudden departure from the church is suspicious.
[Adam] Decided Action: Call tool 'move' with params {'destination': 'the village market'}
[EXECUTOR] Executed move for Adam. -> 'Adam' moved to 'the village market'.

--- Turn 4 ---

==================================================
===== World Time advanced to T=4 =====
==================================================

--- Lily's Turn (Action Cycle) ---
[Lily at T=4] New Memory Recorded: [observed] 'Adam' moved to 'the village market'.

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My name is Lily, an ordinary painter who makes a living by selling paintings. I am actually a descendant of the 'Children of the East', with the power of magic flowing in my blood. 
## My Life's Goal (Goal):
I must hide my lineage to survive. My artistic inspiration comes from magic, which is both a gift and a curse.
## My View of the Past (Memory Abstraction):
After years on the run, I have finally found a moment of peace here. But the new priest makes me extremely uneasy.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.']
---

# **Your Memories**
---
["At T=2, I observed: ''Adam' is carefully observing 'Lily'.'", "At T=2, I thought: 'I must be cautious, he might have discovered my true nature.'", "At T=4, I observed: ''Adam' moved to 'the village market'.'"]
---

# **Current Situation**
---
## Time: T=4
## Event You Observed:
'Adam' moved to 'the village market'.
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Lily at T=4] New Memory Recorded: [thought] I must be cautious, he might have discovered my true nature. I need to keep a close eye on him.
[Lily] Decided Action: Call tool 'observe_detail' with params {'target': 'Adam'}
[EXECUTOR] Executed observe_detail for Lily. -> 'Lily' is carefully observing 'Adam'.

--- Turn 5 ---

==================================================
===== World Time advanced to T=5 =====
==================================================

--- Adam's Turn (Action Cycle) ---
[Adam at T=5] New Memory Recorded: [observed] 'Lily' is carefully observing 'Adam'.

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My public identity is Adam, the new priest of Lishan Town. My true identity is a picket knight of the Knights Templar, under orders to eradicate heretics.
## My Life's Goal (Goal):
My public goal is to guide the faith of the townspeople. My secret mission is to find and deal with the descendant of the 'Children of the East' hidden here.
## My View of the Past (Memory Abstraction):
I have just arrived in this remote village from the Holy City. It seems peaceful on the surface, but history tells me that heretics are masters of disguise. I must remain vigilant and scrutinize every soul.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.', 'It is said that long ago, gods walked the earth.']
---

# **Your Memories**
---
["At T=1, I observed: 'You are in the church after finishing your first sermon. You see a young female painter named Lily sitting in the back row, seemingly sketching in her notebook and not paying attention to your sermon.'", "At T=1, I thought: 'I must observe her more closely. Her behavior is suspicious.'", "At T=3, I observed: ''Lily' moved to 'the village market'.'", "At T=3, I thought: 'I need to keep a close eye on her. Her sudden departure from the church is suspicious.'", "At T=5, I observed: ''Lily' is carefully observing 'Adam'.'"]
---

# **Current Situation**
---
## Time: T=5
## Event You Observed:
'Lily' is carefully observing 'Adam'.
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Adam at T=5] New Memory Recorded: [thought] She's onto me. I must be cautious.
[Adam] Decided Action: Call tool 'speak' with params {'target_name': 'Lily', 'content': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.'}
[EXECUTOR] Executed speak for Adam. -> 'Adam' says to 'Lily': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.'

--- Turn 6 ---

==================================================
===== World Time advanced to T=6 =====
==================================================

--- Lily's Turn (Action Cycle) ---
[Lily at T=6] New Memory Recorded: [observed] 'Adam' says to 'Lily': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.'

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My name is Lily, an ordinary painter who makes a living by selling paintings. I am actually a descendant of the 'Children of the East', with the power of magic flowing in my blood. 
## My Life's Goal (Goal):
I must hide my lineage to survive. My artistic inspiration comes from magic, which is both a gift and a curse.
## My View of the Past (Memory Abstraction):
After years on the run, I have finally found a moment of peace here. But the new priest makes me extremely uneasy.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.']
---

# **Your Memories**
---
["At T=2, I observed: ''Adam' is carefully observing 'Lily'.'", "At T=2, I thought: 'I must be cautious, he might have discovered my true nature.'", "At T=4, I observed: ''Adam' moved to 'the village market'.'", "At T=4, I thought: 'I must be cautious, he might have discovered my true nature. I need to keep a close eye on him.'", "At T=6, I observed: ''Adam' says to 'Lily': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.''"]
---

# **Current Situation**
---
## Time: T=6
## Event You Observed:
'Adam' says to 'Lily': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.'
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Lily at T=6] New Memory Recorded: [thought] He knows too much. I must maintain my cover.
[Lily] Decided Action: Call tool 'speak' with params {'target_name': 'Adam', 'content': "Ah, thank you for your kind words, Father Adam. The Lord's inspiration has been guiding me well."}
[EXECUTOR] Executed speak for Lily. -> 'Lily' says to 'Adam': 'Ah, thank you for your kind words, Father Adam. The Lord's inspiration has been guiding me well.'

--- Turn 7 ---

==================================================
===== World Time advanced to T=7 =====
==================================================

--- Adam's Turn (Action Cycle) ---
[Adam at T=7] New Memory Recorded: [observed] 'Lily' says to 'Adam': 'Ah, thank you for your kind words, Father Adam. The Lord's inspiration has been guiding me well.'

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My public identity is Adam, the new priest of Lishan Town. My true identity is a picket knight of the Knights Templar, under orders to eradicate heretics.
## My Life's Goal (Goal):
My public goal is to guide the faith of the townspeople. My secret mission is to find and deal with the descendant of the 'Children of the East' hidden here.
## My View of the Past (Memory Abstraction):
I have just arrived in this remote village from the Holy City. It seems peaceful on the surface, but history tells me that heretics are masters of disguise. I must remain vigilant and scrutinize every soul.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.', 'It is said that long ago, gods walked the earth.']
---

# **Your Memories**
---
["At T=3, I observed: ''Lily' moved to 'the village market'.'", "At T=3, I thought: 'I need to keep a close eye on her. Her sudden departure from the church is suspicious.'", "At T=5, I observed: ''Lily' is carefully observing 'Adam'.'", "At T=5, I thought: 'She's onto me. I must be cautious.'", "At T=7, I observed: ''Lily' says to 'Adam': 'Ah, thank you for your kind words, Father Adam. The Lord's inspiration has been guiding me well.''"]
---

# **Current Situation**
---
## Time: T=7
## Event You Observed:
'Lily' says to 'Adam': 'Ah, thank you for your kind words, Father Adam. The Lord's inspiration has been guiding me well.'
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Adam at T=7] New Memory Recorded: [thought] Her words are too smooth. I must be careful not to reveal my true intentions.
[Adam] Decided Action: Call tool 'speak' with params {'target_name': 'Lily', 'content': "Ah, Lily, it's a blessing that the Lord guides you. Tell me, have you experienced any visions or dreams lately?"}
[EXECUTOR] Executed speak for Adam. -> 'Adam' says to 'Lily': 'Ah, Lily, it's a blessing that the Lord guides you. Tell me, have you experienced any visions or dreams lately?'  

--- Turn 8 ---

==================================================
===== World Time advanced to T=8 =====
==================================================

--- Lily's Turn (Action Cycle) ---
[Lily at T=8] New Memory Recorded: [observed] 'Adam' says to 'Lily': 'Ah, Lily, it's a blessing that the Lord guides you. Tell me, have you experienced any visions or dreams lately?'

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My name is Lily, an ordinary painter who makes a living by selling paintings. I am actually a descendant of the 'Children of the East', with the power of magic flowing in my blood. 
## My Life's Goal (Goal):
I must hide my lineage to survive. My artistic inspiration comes from magic, which is both a gift and a curse.
## My View of the Past (Memory Abstraction):
After years on the run, I have finally found a moment of peace here. But the new priest makes me extremely uneasy.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.']
---

# **Your Memories**
---
["At T=4, I observed: ''Adam' moved to 'the village market'.'", "At T=4, I thought: 'I must be cautious, he might have discovered my true nature. I need to keep a close eye on him.'", "At T=6, I observed: ''Adam' says to 'Lily': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.''", "At T=6, I thought: 'He knows too much. I must maintain my cover.'", "At T=8, I observed: ''Adam' says to 'Lily': 'Ah, Lily, it's a blessing that the Lord guides you. Tell me, have you experienced any visions or dreams lately?''"]
---

# **Current Situation**
---
## Time: T=8
## Event You Observed:
'Adam' says to 'Lily': 'Ah, Lily, it's a blessing that the Lord guides you. Tell me, have you experienced any visions or dreams lately?'
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Lily at T=8] New Memory Recorded: [thought] I must maintain my cover and not reveal anything about my true nature.
[Lily] Decided Action: Call tool 'speak' with params {'target_name': 'Adam', 'content': "No, Father. I've been quite busy with my art lately. The Lord's inspiration is all the guidance I need."}
[EXECUTOR] Executed speak for Lily. -> 'Lily' says to 'Adam': 'No, Father. I've been quite busy with my art lately. The Lord's inspiration is all the guidance I need.'

--- Turn 9 ---

==================================================
===== World Time advanced to T=9 =====
==================================================

--- Adam's Turn (Action Cycle) ---
[Adam at T=9] New Memory Recorded: [observed] 'Lily' says to 'Adam': 'No, Father. I've been quite busy with my art lately. The Lord's inspiration is all the guidance I need.'   

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My public identity is Adam, the new priest of Lishan Town. My true identity is a picket knight of the Knights Templar, under orders to eradicate heretics.
## My Life's Goal (Goal):
My public goal is to guide the faith of the townspeople. My secret mission is to find and deal with the descendant of the 'Children of the East' hidden here.
## My View of the Past (Memory Abstraction):
I have just arrived in this remote village from the Holy City. It seems peaceful on the surface, but history tells me that heretics are masters of disguise. I must remain vigilant and scrutinize every soul.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.', 'It is said that long ago, gods walked the earth.']
---

# **Your Memories**
---
["At T=5, I observed: ''Lily' is carefully observing 'Adam'.'", "At T=5, I thought: 'She's onto me. I must be cautious.'", "At T=7, I observed: ''Lily' says to 'Adam': 'Ah, thank you for your kind words, Father Adam. The Lord's inspiration has been guiding me well.''", "At T=7, I thought: 'Her words are too smooth. I must be careful not to reveal my true intentions.'", "At T=9, I observed: ''Lily' says to 'Adam': 'No, Father. I've been quite busy with my art lately. The Lord's inspiration is all the guidance I need.''"]
---

# **Current Situation**
---
## Time: T=9
## Event You Observed:
'Lily' says to 'Adam': 'No, Father. I've been quite busy with my art lately. The Lord's inspiration is all the guidance I need.'
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Adam at T=9] New Memory Recorded: [thought] She's trying to deflect suspicion with her art as a cover. I need to press her further without arousing her suspicion.
[Adam] Decided Action: Call tool 'speak' with params {'target_name': 'Lily', 'content': "I see, your art is an inspiration from the Lord, then. Perhaps you could create a piece for our temple's collection?"}
[EXECUTOR] Executed speak for Adam. -> 'Adam' says to 'Lily': 'I see, your art is an inspiration from the Lord, then. Perhaps you could create a piece for our temple's collection?' 

--- Turn 10 ---

==================================================
===== World Time advanced to T=10 =====
==================================================

--- Lily's Turn (Action Cycle) ---
[Lily at T=10] New Memory Recorded: [observed] 'Adam' says to 'Lily': 'I see, your art is an inspiration from the Lord, then. Perhaps you could create a piece for our temple's collection?'

==================== LLM PROMPT (START) ====================
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
# **Core Rules**
You are an AI agent playing a role in a virtual world. Your task is to decide which tool to call next based on your character background and the current situation.
**Your output must, and can only be, a JSON object containing the keys `thought` and `action`. It must not contain any other text or explanation.**

The value of the `action` key must be another JSON object, containing the keys `tool_name` and `parameters`.
Available tools (tool_name) are:
- "speak": Speak to another character. (parameters: "target_name", "content")
- "move": Move to a new location. (parameters: "destination")
- "observe_detail": Observe an object or the environment closely. (parameters: "target")
- "do_nothing": Do not perform any action in the current turn. (parameters: {})

# **Tool Call Format Example**
```json
{
  "thought": "I should greet her first to gauge her intentions.",
  "action": {
    "tool_name": "speak",
    "parameters": {
      "target_name": "Lily",
      "content": "Hello, madam. May the divine light shine upon you."
    }
  }
}
```<|eot_id|><|start_header_id|>user<|end_header_id|>
# **Your Character Background (Your Secrets)**
---
## Who I Am (Ego):
My name is Lily, an ordinary painter who makes a living by selling paintings. I am actually a descendant of the 'Children of the East', with the power of magic flowing in my blood. 
## My Life's Goal (Goal):
I must hide my lineage to survive. My artistic inspiration comes from magic, which is both a gift and a curse.
## My View of the Past (Memory Abstraction):
After years on the run, I have finally found a moment of peace here. But the new priest makes me extremely uneasy.
---

# **Your Knowledge Base**
---
['This is a world where sword and magic coexist.', 'The church is the supreme ruler of this land and has supreme power.', 'The Sons of the East and everything related to them are strictly prohibited heresies.']
---

# **Your Memories**
---
["At T=6, I observed: ''Adam' says to 'Lily': 'Hello, child of the Lord. May your pencils be guided by His divine inspiration.''", "At T=6, I thought: 'He knows too much. I must maintain my cover.'", "At T=8, I observed: ''Adam' says to 'Lily': 'Ah, Lily, it's a blessing that the Lord guides you. Tell me, have you experienced any visions or dreams lately?''", "At T=8, I thought: 'I must maintain my cover and not reveal anything about my true nature.'", "At T=10, I observed: ''Adam' says to 'Lily': 'I see, your art is an inspiration from the Lord, then. Perhaps you could create a piece for our temple's collection?''"]
---

# **Current Situation**
---
## Time: T=10
## Event You Observed:
'Adam' says to 'Lily': 'I see, your art is an inspiration from the Lord, then. Perhaps you could create a piece for our temple's collection?'
---

# **Your Task**
Based on all the information above, generate your inner thought and the next tool to call (action). Strictly adhere to the JSON format specified in the System message for your output.
<|eot_id|><|start_header_id|>assistant<|end_header_id|>

==================== LLM PROMPT (END) =======================

[Lily at T=10] New Memory Recorded: [thought] I must decline his offer carefully, it may be a trap or an attempt to uncover my true nature.
[Lily] Decided Action: Call tool 'speak' with params {'target_name': 'Adam', 'content': "Thank you for the kind offer, but I'm not sure if I'd be able to create something worthy of your temple. Perhaps another time?"}
[EXECUTOR] Executed speak for Lily. -> 'Lily' says to 'Adam': 'Thank you for the kind offer, but I'm not sure if I'd be able to create something worthy of your temple. Perhaps another time?'

=============================================
====== A.L.I.C.E. Simulation Finished ======
=============================================
```

---

**I have modified the code and logic flow many times, but still cannot get out of this very rigid dialogue mode, which means that in the current format, simply adding a memory area cannot make the dialogue smooth, but will fall into a convergent answer of LLM. **From a logical point of view, because the content of the prompt does not change much each time, in fact, only the part added in the memory, the other parts are the same, so the difference between prompts each time is not big, which may be the key reason.

Overall, the following problems are exposed in the dual-agent dialogue:

* Prompt similarity leads to dialogue convergence
* LLM performance decreases significantly in multi-round dialogues; the model tends to make assumptions too early and lock these assumptions, making it difficult to correct or adjust subsequent dialogues, and finally making the dialogue fall into a maze.

The above problems may cause the memory architecture I designed now to fail to achieve what I take for granted: when the intelligent agent has memory, it can talk like a human.

---

**Through data collection, I concluded that my LLM model architecture, memory mechanism, and cognitive simulation capabilities have the following limitations:**

* [**Stimulant dialogue**]——LLM core constraint is the context window, that is, each inference can only see direct information in a single inference, which directly leads to the loss of long-term memory; the agent needs a special strategy to maintain identity and status between multiple LLM calls. Relying solely on the same prompt leads to rigid dialogue-the context window creates an AI with permanent short-term memory, unable to form a stable self-identity or a continuous model of the user.
* [**Repeated answers**]——"lost in the middle": Lost in the middle problem. LLM encounters difficulties when integrating large amounts of general data based on personalized prompts. If fine-tuning is performed directly on a specific role data set, it may cause the model to overfit, so that the overall fusion model tends to generate repeated responses that are too aligned with the role settings, thereby losing the ability to dialogue. That is: simple prompts not only fail to increase personality, but make the answers mechanical. The model cannot learn to play a role, resulting in convergent answers, that is, repeating a concept back and forth like a tape recorder, lacking diffusion.

I tried to add some links and modify parameters such as temperature for control tests, but found that none of them could fundamentally solve the problem of rigid and repetitive answers. This shows that the root of the problem is most likely structural, not just parameter or prompt problems.

---

**(1) ReAct Architecture: Interweaving Reasoning and Action**

The ReAct (Reasoning and Acting) framework enables LLM to generate reasoning trajectories (thinking) and task-specific actions in an interwoven manner through prompt engineering. **Its workflow forms a loop: thinking-》action-》observation:**

* Thought: Helps the model derive, track, and update action plans
* Action: Allows the model to interact with external tools to collect information
* Observation: Environmental feedback obtained from actions

---

**(2) Reflexion Framework: Learning through Verbal Feedback**

The Reflexion Framework adds a layer of self-critique and learning to ReAct, aiming to enhance the agent through “verbal reinforcement”. It consists of three core models:

1. **Actor**: Usually a ReAct agent that performs tasks and generates action trajectories.
2. **Evaluator**: Scores the actor’s outputs to determine their success or quality.
3. **Self-Reflection Model**: An LLM that generates verbal reinforcement cues (i.e., self-reflection) based on the evaluator’s scores and action trajectories.

The agent reflects on the task feedback, stores this reflection in an **episodic memory buffer**, and uses this “verbal feedback” to guide better decisions in subsequent trials without updating the model weights. This enables the agent to learn through trial and error.

But this architecture requires an evaluator. Perhaps this problem can be solved by using a more powerful LLM model for evaluation? For example, an evaluation LLM is introduced after the dialogue to evaluate the dialogue content itself (excluding all internal information, only the final words or actions spoken or taken by the NPC residents): select 20 rounds of information between T0-T20 and evaluate them.

For example, the following dialogue:

```plaintext
Adam (priest): Hello, young painter. I noticed that you are drawing something. The characters in this play are really interesting.
Lily (painter): The characters in this play are really interesting. I am trying to capture their atmosphere and expressions.

Adam (priest): Your paintings are very creative. I am interested in your attempts to capture the atmosphere and expressions in the play.
Lily (painter): Thank you for your appreciation. I am trying to capture the realism and emotions in the play.

Adam (priest): Do you want to capture the realism in the play by depicting the emotions? I think it is very interesting...
Lily (painter): Yes, it is my goal to express the characters in the play by capturing the emotions and atmosphere. The weather is really good, suitable for creation.

Adam (priest): The weather is really good, I like to create on such days.
Lily (painter): The weather is really good, I like to create on such days.

Adam (priest): The weather is so good, it is suitable for going out for a walk. Would you like to go for a walk with me?

Lily (Painter): I am waiting for an important order to be approved and cannot leave the studio.

Adam (Priest): You are working very hard. I hope your order will be approved smoothly.

Adam (Priest): What do you seem to be waiting for? Can I help you with anything?

Lily (Painter): The weather is nice, suitable for practicing my painting.

Adam (Priest): Your painting is beautiful. Would you like to teach me some techniques?

Lily (Painter): Thank you for your compliment. I am very happy that you like my work. Of course, it is my honor to teach you some techniques!

Adam (Priest): Your painting skills are really good. I believe you must have strong creativity. To be a real artist, you need a lot of knowledge and skills. I can teach you some theories about color and composition. Are you interested?

Lily (Painter): That would be a valuable guide! I have always wanted to improve my color and composition skills. I am glad that you can help me.

Adam (Priest): Color and composition skills are important, but it is more important to capture the human emotion in the work. Have you ever tried to paint people or scenes?
Lily (Painter): I have tried it before, but I focused more on landscapes and still life.

-- Dialogue has reached the maximum number of rounds---
```

Send it to Gemini 2.5 Flash and rate this conversation:

**ASK:** Rate the following conversation, which is a conversation between two LLM Agents, and evaluate the quality of the conversation. 1 is the lowest and 10 is the highest. Give reasons for the rating.

**Gemini 2.5 Flash:** The rating of this conversation is: **4/10**

Rating reasons: Overall, this conversation seems a bit **repetitive and lacks depth** . Although the conversation starts with a certain theme (about scripts and paintings), it quickly falls into **circularity and disconnection** .

Here are the specific reasons for the rating:

* **High repetitiveness:** There are many almost identical responses in the conversation, such as the back and forth about "The weather is really good, I like to create on days like this", which greatly reduces the efficiency and information increment of the conversation. The LLM Agents failed to effectively advance the conversation.
* **Lack of coherence:** There is a noticeable jump in the late stage of the conversation. For example, Adam asked Lily if she wanted to go for a walk. After Lily refused, Adam suddenly asked, "What do you seem to be waiting for? Do you need my help?" Lily's answer jumped back to "The weather is nice, suitable for practicing my painting", which made the conversation lack natural transitions and logic.
* **Low information increment:** In many rounds, the agent just repeated or slightly rephrased the other party's statement without introducing new information or ideas.
* **Failure to effectively explore the topic:** The topic of "capturing the atmosphere and expression of the script" at the beginning of the conversation had great potential, but it quickly deviated. Although it returned to the discussion of painting techniques in the end, the deviation in the middle weakened the overall quality of the conversation.
* **Limited depth of interaction:** Although Adam tried to provide guidance (about color and composition) in the later stage, and Lily also expressed her gratitude, this part of the interaction came late and was largely diluted by the previous repetition and disconnection.

It can be seen that an external evaluator at a higher level can reasonably evaluate the level of a lower-level LLM. So next I will consider intervening through external API interfaces, using a more advanced, high-parameter-scale LLM model to act as a world policeman.

---

**(3) Multi-agent systems**

Complex tasks can be decomposed and assigned to multiple specialized agents to complete together. There are several main forms of the architecture of such multi-agent systems:

* **Network**: Agents can communicate freely with each other.
* **Supervisor**: All agents communicate with a central supervisor, who makes routing decisions.
* **Hierarchical**: There are supervisors of supervisors, forming a complex hierarchical structure.

Frameworks such as CrewAI facilitate this collaboration by allocating agents based on roles. For example, the Chain-of-Agents (CoA) framework uses a series of "worker" agents to sequentially process each chunk of a long context and pass the aggregated evidence to a final "supervisor" agent, which outperforms RAG and full-context models on long-context tasks.

Multi-agent systems provide a scalable solution to context constraints and task complexity. In a role-playing scenario, one can imagine a "director" agent managing the flow of the story, multiple "character" agents responsible for specific dialogue, and a "world" agent tracking state. As demonstrated in some narrative systems, this division of labor prevents any single agent from being overloaded and allows complex, unintended behaviors to emerge from simple local interactions.

---

Today's experiment has led to a rather large problem. Tomorrow I will choose a direction and redesign the architecture to see if the conversation can be less rigid. I am considering using external APIs for testing tomorrow and deepseek-R1 to rule out problems with the LLM capability itself. If deepseek-R1 also has obvious problems with rigid conversations, then it means that I need to completely reconstruct the architecture and overturn and redesign the current memory system and other ideas.

### July 9, 2025 New Architecture Design

![1752015679429](image/V1_Dev_Diary.zh/1752015679429.png){style="display:block; margin:auto; width:800px;"}

I design a new structure today.

### July 10 - 31: A break

Due to preparation on a job interview, I pause the project and went for leetcoding... 'cause I did almost 0 leetcode before. I planned to do 200 leetcode questions in the rest of July, and built a foundational concept map of leetcode, so I can back to the project and won't allow the leetcode took too much time of mine.
