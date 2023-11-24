---
{"dg-publish":true,"permalink":"/personal/homelab/plex-meta-manager-install-guide/","created":"2023-10-14T16:17:44.664-04:00"}
---


#Plex

1- before you touch docker, create a text 3 files in notepad titled (config.yml , movies.yml , tv.yml)

2- create a folder called plex meta manager whatever you like

3- place the 3 yml files in that folder

4- download latest docker for plex meta manager

5- to go to your docker and launch the container, go to advance settings, go to volume and select the plex meta manager folder you selected, then the box next to it type "/config/"

6- type in your PUID and PGID (i usually use 1000 for both but do you) and type your TZ

your done for docker, now for the fun stuff, open your config file with any text editor, there is many config files but i will give you what i use

7- paste this into your config.yml but replace all the xxxx with your own info [https://pastebin.com/ituvJWdF](https://pastebin.com/ituvJWdF) for trakt just fill the first two boxes and the rest will be filled automatically ...also remember to use the correct path names for your library

Note: you might have seen in most guides the reference to - git: meisnate12/MovieCharts , ignore it because for some reason this git shit ruins my setup, just follow my steps if you are noob like me

8- paste this into your movie.yml [https://pastebin.com/E62fVjcc](https://pastebin.com/E62fVjcc) which will generate movies collections for all the oscars winning movies, best movies via RT for the years selected, trending movies, popular movies

Note: the lines you see with "#" you need to remove the "#", the reason i have it is because i already ran the code once for these years and i dont to waste 30 mins to run everytime, i assume there is a better way to do it but imma noob..run it once without the # then return the #

9- paste this into your tv.yml [https://pastebin.com/jCY7eUwU](https://pastebin.com/jCY7eUwU) , this will give you trending shows, popular shows, and best new shows of 2021

*Source*: https://www.reddit.com/r/PleX/comments/rtx2e9/guide_plex_meta_manager_step_by_step_setup/