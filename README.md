<div align="center">

# Big Tech is stealing people's time: Show them their abundance
</div>

<div align="center">

  🆓 Free* video and short content creation with AI 🆓

 | Creator                  | GPT Model           | Estimated Monthly Earnings (€) | Source (estimated)                      |
| ------------------------ | ------------------- | ----------------------------- | ---------------------------- |
| RayVentura               | ShortGPT            | €0.45 - €7                    | Socialblade (@AskRedditors)  |
| Su77ungr                 | FreeShortGPT        | €21  -  €341                    | Socialblade (@UnsoundFlash) |

</div>

<div align="center">
  <div style="display: flex;">
    <img width="300" src="https://github.com/su77ungr/FreeShortGPT/assets/69374354/2b98b086-12cc-4dc0-bebd-c34fb856ad01" alt="Image 2"></img>
  </div>
</div>


</div>


### Installation and Use

#### *
The Main branch relies on the paid OpenAI API to work. This has been resolved (not released yet❗) by implementing LlamaCpp for locally hosted Langchain agents instead.
For setup refer to the main [repo](https://docs.shortgpt.ai/docs/how-to-install) and installation [guide](https://docs.shortgpt.ai/docs/how-to-install)

### Upload Automation 

1. Authentification 

Head to the Google API Console https://console.cloud.google.com/ and create a project, add the youtube v3 API (Important: Add scopes for .upload) and web client. 
For more information about the client_secrets.json file format, please visit:
https://developers.google.com/api-client-library/python/guide/aaa_client_s

2. Oauth2.json
   
Once client_secrets.json is gathered from the webclient, run `python3 upload.py` and use the link with the account that is to be automated, This will be saved as *oauth2*.json. You can avoid quota bottlenecks by stacking up projects in the google console and repeat steps before 

3. Automation

Once valid oauth2 credentials exist in the directory you can let this run 100% on autopilot. 

- `ultra.py` is the main script to direct the video production pipeling
- `upload.py` sets the backbone for youtube's v3 api to upload to YouTube without further authentification
- `final_upload.py` combines the finsished product and uploads it to YouTube (title, description, tags get parsed automatically)

Just craft your own bash script or use `automate.sh`


### Upgrades
- access YouTube as provider of video assets, surpassing stock footage by large
- avoids bans by using download streams with PyTube
- avoids YouTube v3 API's rate limit and auth
- avoids Pexels hard rate limit 

### Features 


Inside `api_utils` functions provide utility for working with different APIs. Files: `image_api.py`, `pexels_api.py`,  `youtube_api.py` and `eleven_api.py`. We added  `youtube_api.py` to source video assets directly from YouTube. Feel free to modify `the _generateVideoUrls` function for the hierachy of video asset sources. 

-  #### `search_videos_YouTube(query_string)`
  
      The search_videos_YouTube function takes a query string as input and searches for a video on YouTube based on that query. It returns the URL of the first search result if found, or None if no video is found.
      
      Integration of `shortGPT.api_utils.youtube_api`, which serves as an additional source for gathering footage based on the queried keyword. This is particularly useful when dealing with niche / comedy / meme topics where stock footage is not available. If nothing matches we backtrack to the pexels API. 

-  #### `triage_videos_Youtube(expected_score_parameter)` ❗not released yet

### Demo

demo_new shows the accuracy of the newly added youtube query policy ***without*** further guidance, backtesting or content analysis. This can be improved by adding a content triage based on Clip2 and transcript analysis. 



https://github.com/su77ungr/FreeShortGPT/assets/69374354/4b561ba1-008a-4b91-b97b-eb14ec37f74a



deprecated_demo shows the accuracy of Google's YouTube v3, you can find it here: https://vimeo.com/851101834?share=copy.
