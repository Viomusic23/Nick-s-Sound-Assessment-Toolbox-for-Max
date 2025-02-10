## Welcome to the NSAT for Max 8 Toolbox. 
I created this soundscape assessment patch as part of my Final Year Project, "", for my BSc Music Technology course at Birmingham City University. I'm currently looking at expanding my research into a better academic paper, hence developing these patches into more user-friendly Snippets in Max 8. If you wish to read my research project it can be found at: 

## About NSAT
The idea is to use this patching method to create a cohesive soundscape asessment questionaire using Max 8, in conjuction with the Mira mobile app or MiraWeb on a portable device, controlled by the test participant, with oversight from the person conducting the tests, along with a presenting screen for displaying videos or images. The 'controller' has full access to what the participant is seeing but should let the participant take themselves through the assessment at their own pace, with their own answers to the questions presented. 
The questionaire is based on the ISO(####) standard for soundscape assessments, as well as the Mitchell et al. paper "How to analyse and represent quantative soundscape data", with the exported text format being able to paste directly into Excel for displaying using Mitchell et al.'s methods for data representation. 

The questionaire is also programmed to be double blind creating a unique question order for each test participant, to eliminate any form of biases between audio clips. However, the random seed is also used internally to always ensure your results from the assessment come back in the same order. 

## Getting Started:
- Download the "Snippets" folder from this repo.
- Navigate to your Max 8 Snippets folder, by default this should be /Documents/Max 8/Snippets.
- Drag and drop the NSAT.maxsnip files into "Snippets" and Launch Max 8. 

The NSA Toolbox will now be accessible from the Max editor.

## Making a new Soundscape Assessment:
If you are looking to conduct a basic soundscape assessment this will take you through the correct (current) set up method for creating the logic behind the assessments.

- Create a new Patch.
- Click to open the Snippets Menu. <img width="34" alt="Max 8 Snippets Menu Icon" src="https://github.com/user-attachments/assets/c9f0dff8-ee4a-4d83-b82c-482931c7ce35" />
- Drag "NSAT-QuestionaireBase" into Patch.

  This will serve as the main internal logic for the questionaire form submission, presentation and result collation.
  To configure the Questionaire Base Snippet:
- Click the "Change Keybind" toggle object.
- Press the key you would like to use to refresh the entire test, between testing partcipants.
  This is now the Key you will use when asked to ***Refresh*** the patch.
- If at this stage you know how many question slides you will be needing (- the Welcome and Thank You splash screens) you can change the "Max Slides" number object, default 6, to reflect this. If not please remember to **keep updating this number as more slides are added** else they won't be presented to the test participant. (this step will be fixed in a future update!)

- Next, reopen the Snippets Menu.
- Drag NSAT-AudioOutput into Patch.

  This will process the output routing and volume calibration for your patch.
- Set the multichannel audio format you will be importing into Max (Stereo, Surround, etc.)
- Set the desired audio output format you will be using to present.
- Check this has linked correctly in the graphic 'crosspatch' object. If there are any issues, you can manipulate the nodes by clicking on each of the desired circles. [Crosspatch Reference](https://docs.cycling74.com/legacy/max8/refpages/crosspatch)

  (If you are a BCU student in the SoundLab, there is currently two ways of outputting to the speakers:

  i)  Soundlab in 5.1, will route a 5.1 file to a rough approximation of 5.1 speaker arrangements for playback, or

  ii) Custom routing from your audio input channels to specific speakers.

  This will be fixed in a future push to work with the "Loader Patch")

- Next, reopen the Snippets Menu.
- Select the Snippet for the required audio/visual configuration (for example, NSAT-1Vis1Aud, for 1 video and 1 audio clip)
- Drag into Patch.
- The sections with Green Text require modifications
    * Master Slide Numbers (this will be the internal logic for which slide you want this to be, and the order it will appear in your results, starting from the number 1), Simply change the number of the Loadmess object.
    * Drag/Drop in your video or Image. Currently an image is required to play audio 'in sync' as this was originally designed for just my purposes but this will be fixed in future.
    * Drag/Drop in your audio clips.
    * Change the question 'Send' object variable to send to the results patch. (this will also be removed in future, but for now if only presenting with one Snippet module this can be left as default "Ex_Results"
- ***Refresh before adding any other Snippets*** This is very important for the logic of the Mira Frames, to assign them to the correct numbers first time. For this reason you must also make sure to change the slide numbers of each subsequent Questions Snippet.
- Test that audio/video plays when clicking the play button in presentation mode (may need to click twice)

 Repeat adding Question Snippets until you have completed your questionaire. Feel free to change the layout or design of the Mira frames in presentation view to your desired look. 

 Remember to refresh in between adding questions and adding more to the total slides in the QuestionaireBase Snippet Module.

 ## The Results Screen
 When you're happy with your questionaire, navigate to the "Results" Tab at the top of the Patch (this will have been created when adding the QuestionaireBase Module).

 To configure this section enter edit mode. You will see the "Ex_Results" receive object inputting to a message box. This is the layout you will need to copy with the correct bang order, with the correct Send/Receive variables in order to collate your candidates' results.
 This process will be made simpler in a future push. For now, see the demo patch to see how this is configured. 

 When your test participants have completed the test, press the Big Red Button<sup>TM</sup> to see your results as a text object list. This can be copy/pasted into an Excel Sheet, in the format of the Demo Workbook, or saved as a .csv. Just be sure to save your candidates results before Refeshing for the next candidate.
 
 
To load results, click the red circle and results for that participant will open in a text file - these can then be copied to csv
