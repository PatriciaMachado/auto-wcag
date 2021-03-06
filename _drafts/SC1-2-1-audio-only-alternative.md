---
rule_id: SC1-2-1-audio-only-alternative
name: Alternate version of prerecorded audio-only
test_mode: manual

criteria:
- 1.2.1 # Audio-only and Video-only (Prerecorded) (Level A)

authors:

---

## Description

This test checks that for prerecorded audio-only content an alternative version exists, which is relevant and descriptive for the audio-only content.

## Background

- [G158: Providing an alternative for time-based media for audio-only content](http://www.w3.org/TR/2014/NOTE-WCAG20-TECHS-20140916/G158)
- [F30: Failure of Success Criterion 1.1.1 and 1.2.1 due to using text alternatives that are not alternatives (e.g., filenames or placeholder text)](http://www.w3.org/TR/2014/NOTE-WCAG20-TECHS-20140916/F30)
- [F67: Failure of Success Criterion 1.1.1 and 1.2.1 due to providing long descriptions for non-text content that does not serve the same purpose or does not present the same information](http://www.w3.org/TR/2014/NOTE-WCAG20-TECHS-20140916/F67)

## Assumptions

- The audio is not a media alternative for another media
- The audio may be played misusing a video element, possibly combined with a still image. This is not covered by this test-case.
- Audio generated by client-side-script on runtime is not covered by this test-case.

## Test properties

| Property          | Value
|-------------------|----
| Test name         | Alternate version of prerecorded audio-only
| Test requirement  | 1.2.1 Audio-only and Video-only (Prerecorded)
| Test mode         | manual
| Test environment  | rendered page + server connection
| Test subject      | single web page
| User expertise and skills | no prior knowledge
| User profile      | Requires hearing

## Test procedure

### Selector

Test mode: [manual][MANUAL]

All pages including elements capable of playing audio.

Those can be identified by including

- `audio` elements
- elements having resources with a mimetype containing the string "audio" in their http-header
- elements having an attribute value containing a media file format, such as .wav, .aif, .aiff, .mp3, .ogg, .oga, .mov, .mid, .rm, .ra, .ram, .wma, .asf, .swf, .dcr, .avi, .mpg, .mpeg, .mp4, .m4v, .webm, .flv, .isma   (`//*[contains(@*,'.mid') or contains(@*,'.mp3') or ... ]`)

For each selected item, go through the following steps:

### Step 1

Test mode: [manual][MANUAL]

Check that the audio-only content is prerecorded.

**User Input Question:**

| Property             | Value
|----------------------|---------
| Presented item       | Whole page
| Requires context     | yes
| Requires Interaction | yes
| Question             | Is the audio-only content prerecorded?
| Help                 | Usually live content is explicitly marked as such. You can also try to navigate to the end of the media. On live content you will not be able to. If the content is prerecorded, select “Yes”. Else select “No”.

If yes, continue with [Step 2](#step-2)

else return:

| Outcome  | Inapplicable
|----------|-----
| Testcase | SC1-2-1-audio-only-alternative
| ID       | SC1-2-1-audio-only-alternative-inapplicable1

### Step 2

Test mode: [manual][MANUAL]

Check that the prerecorded audio-only content is not purely decorative and has relevant information for the context of the web page.

**User Input Question:**

| Property             | Value
|----------------------|---------
| Presented item       | Whole page
| Requires context     | yes
| Requires Interaction | yes
| Question             | Is the audio-only content solely for decorative purposes and does not contain information, e.g. background music without any additional meaning for the page?
| Help                 | If the audio-only content is purely decorative and does not contain relevant information for the context of the web page select “Yes”. Else select “No”.

If yes, return:

| Outcome  | Passed
|----------|-----
| Testcase | SC1-2-1-audio-only-alternative
| ID       | SC1-2-1-audio-only-alternative-pass1

Else continue with [Step 3](#step-3)

### Step 3

Test mode: [manual][MANUAL]

Check that there is an alternative version available for the prerecorded audio-only content.

**User Input Question:**

| Property             | Value
|----------------------|---------
| Presented item       | Whole page
| Requires context     | yes
| Requires Interaction | yes
| Question             | Is there an text version for the audio-only content available?
| Help                 | The alternative version needs to tell the same story and present the same information as the prerecorded audio-only content. It should not contain more information than the audio-only content itself. If there is an text version available directly near the audio-only content, which sufficiently describes and conveys all information of the the audio-only content, select “Yes”. Else select “No”.

If yes, return:

| Outcome  | Passed
|----------|-----
| Testcase | SC1-2-1-audio-only-alternative
| ID       | SC1-2-1-audio-only-alternative-pass2

Else return:

| Outcome  | Failed
|----------|-----
| Testcase | SC1-2-1-audio-only-alternative
| ID       | SC1-2-1-audio-only-alternative-fail1
| Error    | Missing or insufficient alternative version.

[AUTO]: ../pages/test-modes.html#automatic
[MANUAL]: ../pages/test-modes.html#manual