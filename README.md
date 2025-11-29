%%writefile README.md
# Book-to-Film Adaptation Analysis App

## Project Overview
The 'Book-to-Film Adaptation Analysis App' is a Streamlit application designed to assist users in evaluating the cinematic potential of a book summary. Its primary goal is to leverage large language models to generate detailed analyses across various aspects crucial for film adaptation, including cinematic themes, character psychology, visual style, genre, and key scenes, thereby streamlining the pre-production assessment process for filmmakers and storytellers.

## Key Features

### Core Application Functionalities:

1.  **Cinematic Summary Generation:**
    *   **Purpose:** This feature takes a raw, detailed book summary and processes it to create a concise, cinematic version. It filters out non-essential details and highlights aspects most relevant for a film adaptation, making it easier for subsequent analysis steps.

2.  **Cinematic Analysis:**
    *   **Purpose:** This component delves into the narrative to extract crucial cinematic elements. It identifies:
        *   **Cinematic Theme:** The overarching message or idea suitable for film.
        *   **Protagonist:** The main character, their motivations, and journey.
        *   **Antagonist:** The opposing force, whether a character, system, or internal struggle.
        *   **Moral Tension:** The ethical dilemmas and conflicts within the story.
        *   **Emotional Question:** The core emotional conflict or inquiry posed by the narrative.

3.  **Logline and Alternate Concepts:**
    *   **Purpose:** This feature focuses on the high-level pitch for a film adaptation. It generates:
        *   A compelling **short-film logline:** A one-sentence summary capturing the essence of the story, protagonist, and conflict.
        *   **Two alternate short-film concepts:** Brief outlines for different interpretations or approaches to adapting the story, offering creative variations.

4.  **Visuals and Opening Shot:**
    *   **Purpose:** This functionality translates the literary summary into visual film language, providing insights into potential aesthetic choices. It covers:
        *   **Camera Style:** Recommendations for camera movement, angles, and shot types.
        *   **Color & Lighting:** Suggestions for the visual mood, palette, and illumination techniques.
        *   **Sound Design:** Ideas for auditory elements, music, and ambient sounds.
        *   **Opening Shot:** A detailed description of the film's potential first shot, setting the tone and visual style.

5.  **Character Psychology Analysis:**
    *   **Purpose:** This feature provides a deeper understanding of the main characters' inner workings, crucial for compelling portrayals. It analyzes:
        *   **Protagonist Goal, Need, Wound:** What the protagonist actively seeks, what they truly lack, and past traumas influencing them.
        *   **Antagonist Worldview:** The core beliefs and philosophies driving the antagonist's actions.

6.  **Genre Analysis:**
    *   **Purpose:** This component categorizes the story within film genres and identifies its potential audience. It determines:
        *   **Primary Genre:** The most dominant film genre.
        *   **Secondary Genres:** Supporting genres that also apply.
        *   **Target Audience:** A description of the likely demographic that would be drawn to the film adaptation.

7.  **Key Scenes:**
    *   **Purpose:** This feature pinpoints the most critical moments in the narrative, essential for structuring a screenplay. It identifies and briefly describes 3-5 pivotal or key scenes from the cinematic summary.

## Technologies Used

1.  **Primary Programming Language:** Python
2.  **AI Framework for LLM Applications:** LangChain
3.  **LLM API Provider:** Groq API
4.  **Web Framework for Interactive UI:** Streamlit
5.  **Tool for Exposing Local App (Colab):** ngrok

## Setup Instructions
#### Instructions
1. Ensure you have Python 3.8 or higher installed on your system. You can verify this by running `python --version` or `python3 --version` in your terminal.
2. Obtain an API key from Groq to use their language models. You will also need an ngrok authentication token if you plan to run this application in a local environment and expose it publicly, or in a Colab environment.
3. Create a new directory for your project and navigate into it using your terminal.
4. (Optional, but recommended) Create and activate a virtual environment for the project to manage dependencies:
    - `python -m venv venv`
    - `source venv/bin/activate` (on Linux/macOS)
    - `.\venv\Scripts\activate` (on Windows PowerShell)
5. Install the necessary Python libraries using pip:
    - `pip install langchain langchain-groq python-dotenv streamlit pyngrok`
6. Create a new file named `app.py` in your project directory and copy the complete Streamlit application code into it. This code includes the LLM setup, prompt definitions, the `book_to_film` function, and the Streamlit UI logic, as previously provided in the notebook.

## Running the Application

### Instructions
To launch the Streamlit application:

#### 1. Local Development Environment
If you are running this application in a local environment (e.g., on your computer):

*   **Save the code:** Ensure all the Python code for the application is saved in a file named `app.py`.
*   **Open Terminal/Command Prompt:** Navigate to the directory where `app.py` is saved.
*   **Run the command:** Execute the following command:
    ```bash
    streamlit run app.py
    ```
*   **Access the app:** Streamlit will automatically open a new tab in your web browser with the application running.

#### 2. Google Colab Notebook Environment
If you are running this application within a Google Colab notebook:

*   **Install `pyngrok`:** This library is used to create secure tunnels to expose your local server to the internet. If not already installed, run:
    ```python
    !pip install pyngrok
    ```
*   **Import `ngrok` and Authenticate:** You need an ngrok authentication token to use its services. Replace `'YOUR_NGROK_AUTH_TOKEN'` with your actual token (you can find this on your [ngrok dashboard](https://dashboard.ngrok.com/auth/your-authtoken)) and run the following code:
    ```python
    from pyngrok import ngrok
    
    NGROK_AUTH_TOKEN = 'YOUR_NGROK_AUTH_TOKEN' # Replace with your token
    ngrok.set_auth_token(NGROK_AUTH_TOKEN)
    print("ngrok authentication token set.")
    ```
*   **Run `app.py` in the Background:** Execute the Streamlit application as a background process. This command runs the `app.py` script and redirects its output to `/dev/null` to keep the Colab output clean.
    ```bash
    !streamlit run app.py &>/dev/null&
    ```
*   **Expose with `ngrok` and Get Public URL:** This step creates a public URL that tunnels to your Streamlit app running on port `8501` (Streamlit's default port). The URL will be printed for you to access.
    ```python
    from pyngrok import ngrok
    ngrok.kill() # Optional: Kills any previous ngrok processes
    public_url = ngrok.connect(addr='8501', proto='http')
    print(f"Streamlit App URL: {public_url}")
    ```
*   **Access the app:** Click on the `Streamlit App URL` provided in the output to access your application.

## Usage Guide
## How to Use the Book-to-Film Adaptation Analysis App

This guide will walk you through the steps to use the Streamlit application to analyze a book summary for its film adaptation potential.

### Step-by-Step Usage:

1.  **Access the Application**: Navigate to the public URL provided by ngrok. In this case, the URL is: `https://distractedly-groovelike-pandora.ngrok-free.dev`. Open this link in your web browser.

2.  **Locate the Input Area**: On the application's main page, you will find a large text area labeled 'Enter Book Summary here:'.

3.  **Paste Your Book Summary**: Copy the summary of the book you wish to analyze and paste it into the designated text area.

4.  **Initiate Analysis**: Click the blue button labeled 'Generate Film Adaptation Analysis'.

5.  **Wait for Results**: The application will display a spinner indicating that the analysis is in progress. Please wait a few moments for the AI model to process your summary.

6.  **Review the Analysis**: Once the analysis is complete, the results will appear below the input area, divided into several sections:
    *   **Cleaned Cinematic Summary**: A concise, cinematic version of your original summary.
    *   **Cinematic Analysis**: Insights into cinematic theme, protagonist, antagonist, moral tension, and emotional question.
    *   **Logline and Alternate Concepts**: A short-film logline and two alternative short-film ideas.
    *   **Visuals and Opening Shot**: Suggestions for camera style, color & lighting, sound design, and an opening shot description.
    *   **Character Psychology Analysis**: An examination of the protagonist's goals, needs, and wounds, and the antagonist's worldview.
    *   **Genre Analysis**: Identification of primary and secondary genres and the likely target audience.
    *   **Key Scenes**: A list of 3-5 pivotal or key scenes with brief descriptions.

Read through each section to gain a comprehensive understanding of your book's potential as a film adaptation.

## Future Enhancements

Here are some potential enhancements for the 'Book-to-Film Adaptation Analysis App' to make it more robust, interesting, and user-friendly:

*   **Enhanced Input Methods**: Allow users to upload text files (e.g., .txt, .docx, .pdf) or directly link to online book summaries instead of just pasting text into the text area.
*   **LLM Model Selection and Customization**: Provide options for users to select different underlying LLM models (e.g., other Groq models, OpenAI, Anthropic, etc.) or to fine-tune prompt parameters (temperature, max tokens) to explore varied analysis styles.
*   **User Feedback Mechanism**: Implement a system where users can rate the quality and relevance of the generated analysis, helping to improve the model or prompts over time.
*   **Visual Integration**: Integrate a feature to generate mood boards, concept art, or visual themes based on the 'Visuals' analysis, possibly by connecting to image generation APIs (e.g., DALL-E, Midjourney).
*   **Comparison Tool**: Allow users to analyze multiple book summaries and compare their film adaptation potentials side-by-side.
*   **Multi-language Support**: Extend the application to support book summaries and analysis generation in multiple languages.
*   **Dialogue and Scene Generation**: Add a feature to generate short character dialogues or brief scene excerpts based on the 'Character Psychology' and 'Key Scenes' analysis, providing a more immersive creative tool.
*   **Interactive Storyboarding**: Develop a feature that could outline a basic storyboard based on the key scenes, potentially with simple visual cues.


