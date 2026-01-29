# Snake: Windows Media Controls Edition
**_"Have you ever wanted to play snake inside the album art of the windows media controls overlay? Probably not, but now you can!"_**

## What is This?
This is a fully functional Snake game that lives where it shouldn't: inside the Windows Media Controls Overlay (`Win + A`). It works by hijacking the browser's MediaSession API and HTML5 Canvas to stream a live game feed as "Album Artwork" while a silent track plays in the background—tricking Windows into thinking a classic arcade game is actually just a silent song that is pretty indecisive about what its metadata is.

The game "screen" is displayed where the album art would normally go, score is tracked in the song title, and high score in the artist name. Kebyoard media buttons (or the mouse) are used to control the game.

<table>
  <tr>
    <td valign="venter">
      <br> 
        <div align="center">
          <img width="390" height="635" alt="website ui" src="https://github.com/user-attachments/assets/b744491a-4f67-4fcd-be4d-1e48dbc291d0" />
        <br>
        <p><sup><i>Figure 1: Screenshot of the webpage UI.</i></sup></p>
      </div>
    </td>
    <td width="400">
      <div align="center">
        <img width="390" src="https://github.com/user-attachments/assets/306f1572-e59c-46eb-a393-93472286f782" alt="snake game running" />
        <br>
        <p><sup><i>Figure 2: Snake running in the Windows Media Controls Overlay.</i></sup></p>
      </div>
    </td>
  </tr>
</table>

## How to Play
1. Visit the site [HERE](https://thegoodjakeward.github.io/snake_windows_media_controls_edition/).

2. Initialize: Choose your settings (optional) and then click the big green button to link the system.

3. Open the "Game Screen": Press `Win + A` on your keyboard.

4. Press `Prev Track (⏮︎)` or `Next Track (⏭︎)` to start.


### The Controls*:

- `Prev Track (⏮︎)`: Turn LEFT

- `Next Track (⏭︎)`: Turn RIGHT

- `Play/Pause (⏵︎/⏸︎)`: Cycle background colors (by matching the background to the color of the overlay, it makes the flickering more bearable).

**The Goal: Eat Food. Don't hit yourself. Get the high score.**

<sup>*Note: Some keyboards (like mine) will require holding down the `Fn` key in order to use the media buttons. See the image descriptions below for a few more thoughts on keyboard variations.</sup>


<table>
  <tr>
    <td width="300">
      
  ![keyboard variant 1](https://github.com/user-attachments/assets/2c1d7e9c-caaa-4c81-a80b-ea87b9145ae4)

  </td>
    <td valign="top">
      <h4>Keyboard Variation #1</h4>
      <p>Of the 4 or 5 keyboards I found lying around my house, this one has the most media buttons, with buttons for Stop, Prev Track, Play/Pause, and Next Track. Annoyingly though, it requires holding down Fn to use these media buttons, which means I was required to hold down Fn for the entirety of my snake-playing experience.</p>
    </td>
  </tr>

  <tr>
    <td width="300">
      
  ![keyboard variant 2](https://github.com/user-attachments/assets/47bab3af-7624-4ff6-9de1-e20799c0eb79)

  </td>
    <td valign="top">
      <h4>Keyboard Variation #2</h4>
      <p>The second keyboard type I found in my house was missing the Stop media button, but that button is not currently in the game anyway so that's fine. This keyboard also doesn't require holding the Fn key to use the media buttons. Overall, 10/10 experience playing snake in the Windows Media Controls Overlay with this keyboard.</p>
    </td>
  </tr>

  <tr>
    <td width="300">
      
  ![keyboard variant 3](https://github.com/user-attachments/assets/93d42f09-813b-4e90-9273-3cb3c663dade)

  </td>
    <td valign="top">
      <h4>Keyboard Variation #3</h4>
      <p>This keyboard is a few media buttons short of a snake game, if you know what I mean. With only the play/pause button to work with, this keyboard is only capable of changing the background color in the game, which doesn't earn you any points unfortunately. Playing snake with this keyboard is not going to be possible. I'll also point out that not a single one of the keyboards I own have the media buttons on the same F-keys so there seems to be no industry standard.</p>
    </td>
  </tr>

  <tr>
  <td width="300">

  <video src="https://github.com/user-attachments/assets/e022013b-891d-4742-aeee-7fc785bc71a4" width="100%" controls>
  </video>



  </td>
    <td valign="top">
      <h4>Keyboard Variation #4</h4>
      <p>The last variation is actually no keyboard at all! After I had already completely finished this project, it occurred to me that I might be able to just use my mouse and click on the media control buttons in the overlay to control the snake. Turns out, it worked! And better yet, it worked without me having to make any further modifications to my code! So if your keyboard doesn't have the proper media buttons to play the game, there is hope for you yet. Keyboard is still the vastly easier way to play in my humble opinion, but you fps gamers can give mouse controls a shot, I guess.</p>
    </td>
  </tr>
</table>

## The Out-Of-Focus Paradox

When I first started this, I was so focused on _showing_ the game in the overlay that I forgot I actually had to _play_ it. 

I quickly ran into a major problem: **The Focus Paradox**. 
- To use `W` `A` `S` `D` or `←` `→` `↑` `↓` keys, the browser tab needs to be in focus.
- To see the game, you have to open the `Win + A` overlay.
- Opening the overlay **removes focus** from the browser.
- Clicking the browser to get focus back **closes the overlay**.

It was a nightmare. I could either play the game without seeing it, or see the game without playing it.

Then I found the loophole: **Media Keys**. They are the only inputs allowed to talk to a background webpage without closing the media overlay. So, while it feels a little weird to "Skip Track" to turn right (especially when I also have to hold down the `FN` key to use the media keys on my keyboard), it’s the _key_ 😏 to making this project possible ~~and the only way to keep the dream alive~~. (Edit: Turns out you can use the mouse too, so it's not the _only_ way, but it's the _preferable_ way in my opinion.)

## The Flickering Problem

Before you say anything, I know the flickering can be a little annoying. It seems to be a limitation of how the overlay refreshes the album art. How dare the Windows 11 developers not keep gaming in mind when designing the Media Controls Overlay!!! 

I was able to slightly mitigate flickering by giving the option to change the background color of the game. If you match the game's background color to the color of the Media Controls Overlay, the flickering is a lot less noticable because only the snake and food (and outside border) flicker instead of the whole image. It's not perfect, but it probably goes without saying that we are gaming in uncharted territory here, so there's gonna be a few quirks.


<table>
  <tr>
    <td width="500">
      <video src="https://github.com/user-attachments/assets/23d8c502-8069-4dfa-9732-4ad455f75649" width="100%" controls>
      </video>
    </td>
    <td valign="center" style="padding-left: 15px;">
      <p>
        If you click play on the video to your left, you'll see the flicker correction in action. It starts off with a black background where the flickering is at its worst, and then I repeatedly hit Play/Pause to change the background color to match the overlay's color, which certainly helps.
      </p>
    </td>
  </tr>
</table>


## License
This project is licensed under the MIT License. You’re free to fork it, break it, or turn it into the next big thing (unlikely).

However, if this code helps you out (or makes you laugh), giving a little shout-out or a link back to this repo would be awesome. It’s good for the soul—and my GitHub ego.
