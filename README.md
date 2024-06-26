# ChatGPT-AutoHotkey-Utility-Offline

[⏬ Download here](https://github.com/AleksKlomp/ChatGPT-AutoHotkey-Utility-Offline/releases/latest)

An AutoHotkey v2 script that can use both the ChatGPT API as well as LM Studio, a program that enables you to run LLMs on your laptop, entirely offline. Process text using various language models through an OpenAI compatible local server that you can connect to without internet!

![GIF](https://github.com/AleksKlomp/ChatGPT-AutoHotkey-Utility-Offline/assets/144496933/8f02fe29-ebbe-49a8-9f3e-0c0fb23b18bf)

## Added features
- No internet connection required (just start a local HTTP server in LM Studio)
- Use any LLM
- You can drag the GUI window to any location, or minimize it so it does not block the screen. Auto Copy-Paste will still work as intended.
- Copy response text automatically into the Clipboard
- Paste response text automatically into the edit field of any program

## How to use

1. Install [AutoHotkey v2](https://www.autohotkey.com/). Note that this script will not work on earlier versions of AutoHotkey.
2. Install [LM Studio for Windows](https://lmstudio.ai/).
3. "Search" for any compatible model files that you can download in the app (e.g. lmstudio-community/Meta-Llama-3-8B-Instruct-GGUF)
![LM Studio](https://github.com/AleksKlomp/ChatGPT-AutoHotkey-Utility-Offline/assets/144496933/e2b5f76c-0714-49de-aa9b-55322d775af9)
5. Click on "Local Server" and "Select a model to load". (The server should now begin running on port 1234)
![LM Studio](https://github.com/AleksKlomp/ChatGPT-AutoHotkey-Utility-Offline/assets/144496933/8091df2b-f43d-49a0-88e1-9af2182ef6c8)

7. OPTIONAL: Copy your OpenAI API key [here](https://platform.openai.com/account/api-keys) (you may need to create a new secret key‍). Note that this is not needed if you do not intend to use ChatGPT.
8. OPTIONAL: Open `ChatGPT AutoHotkey Utility.ahk` using your favorite text editor
9. OPTIONAL: Paste your OpenAI API key on the `OpenAI_API_Key` variable

![API Key](https://github.com/AleksKlomp/ChatGPT-AutoHotkey-Utility-Offline/assets/144496933/f8ad2e2f-0989-4b96-a61a-842cef92f2f2)

5. Launch `ChatGPT AutoHotkey Utility.ahk`
6. Highlight a text that you want to process using ChatGPT API and press the `back quote` key to bring up the menu

![image](https://github.com/kdalanon/ChatGPT-AutoHotkey-Utility/assets/123705491/7615e7b5-c4f0-4a8f-9608-669a021ac38d)

(Image from [emacs.stackexchange.com](https://emacs.stackexchange.com/questions/16749/how-to-set-emacs-to-recognize-backtick-and-tilde-with-a-colemak-keyboard-layout))

## Customizing menu, prompts, APIs, set timeouts and hotkey

You can customize prompts and the menu order by doing the following:

### Menu

Under `Menus and ChatGPT prompts`, add a menu by adding this code:

```AutoHotkey
MenuPopup.Add("&8 - Text_To_Appear", Function_To_Execute_When_Selected)
```

The character next to the "and" sign (&) is the hotkey for that particular menu that, when pressed, activates it.

You can also add a line separator using this code:

```AutoHotkey
MenuPopup.Add()
```

### Prompt

You can add a prompt using this code:

```AutoHotkey
Function_To_Execute_When_Selected(*) {
    ChatGPT_Prompt := "Your prompt here:"
    Status_Message := "Status message that will show while processing the request"
    API_Model := "gpt-4" ; or API_Model := "gpt-3.5-turbo"
    ProcessRequest(ChatGPT_Prompt, Status_Message, API_Model, Retry_Status)
}
```

### APIs

You can edit the API used for each prompt by changing the `API_Model` under each prompt. Visit [this page](https://platform.openai.com/docs/models/gpt-4-turbo-and-gpt-4) to explore a selection of available API models.

![76IxQa4](https://github.com/kdalanon/ChatGPT-AutoHotkey-Utility/assets/123705491/7bd23815-78d8-4629-b69b-7fcea3be5f28)

### Set timeouts

By default, HTTP_Request.SetTimeouts is set to a whopping 5 minutes. This is because LLMs will run slowly depending on your laptop specs. This will be different for everybody. You can play around with this number to suit your own needs.

![SetTimeouts](https://github.com/AleksKlomp/ChatGPT-AutoHotkey-Utility-Offline/assets/144496933/df6a4e78-7d44-4280-9101-d4c4838ce419)

### Hotkey

You can change the activation hotkey under Hotkey. See [here](https://www.autohotkey.com/docs/v2/KeyList.htm) for the list of possible hotkeys.

![image](https://github.com/kdalanon/ChatGPT-AutoHotkey-Utility/assets/123705491/da257ab3-05d0-4779-87a2-0a2ba6270255)

## Credits

- [kdalanon](https://github.com/kdalanon/ChatGPT-AutoHotkey-Utility) for the original ChatGPT-AutoHotkey-Utility script
- [AutoHotkey-JSON](https://github.com/cocobelgica/AutoHotkey-JSON) library
- [ai-tools-ahk](https://github.com/ecornell/ai-tools-ahk) for the inspiration
- [Microsoft Copilot](https://www.bing.com/images/create/extremely-simple-graphic-of-the-writing-hand-emoji/1-667c7f1955cd40c68f0fc7032f3efaa5?id=twRLOcxSHp1iYCRcMv4ufw%3d%3d&view=detailv2&idpp=genimg&idpclose=1&thId=OIG2.Mg_FIsVADFVGEbDkoeFz&frame=sydedg&FORM=SYDBIC) for the icon
