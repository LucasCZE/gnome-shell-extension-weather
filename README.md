![Screenshot](https://github.com/neroth/gnome-shell-extension-weather/raw/master/data/Screenshot.png)

**gnome-shell-extension-weather** is a simple extension for displaying weather informations from several cities in GNOME Shell.

Compared to the original version, this fork brings you : multiple city, no WOEID, a symmetric style, and a settings panel in JavaScript (Seed).

Currently, the weather report including forecast for today and tomorrow is fetched from [Yahoo! Weather](http://weather.yahoo.com/).

----

# Installation

**At end of installation restart GNOME Shell (`[Alt]+[F2]`, `r`) and active the extension in `gnome-tweak-tool`.**

## Package manager

### [Arch Linux](https://aur.archlinux.org/packages.php?ID=56028)

Make package form AUR and install.

	wget https://aur.archlinux.org/packages/gn/gnome-shell-extension-weather-neroth-git/gnome-shell-extension-weather-neroth-git.tar.gz
	tar xvzf gnome-shell-extension-weather-neroth-git.tar.gz
	cd gnome-shell-extension-weather-neroth-git && makepkg -si

### [Ubuntu](https://launchpad.net/~xeked/+archive/gnome/+packages)

Add the PPA **ppa:xeked/gnome** in your source list, add key **0B5C004838624188** form `keyserver.ubuntu.com`, update package list and install **gnome-shell-extension-weather**.

	sudo add-apt-repository ppa:xeked/gnome
	sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0B5C004838624188
	sudo apt-get update
	sudo apt-get install gnome-shell-extension-weather

### [ALT Linux](http://packages.altlinux.org/en/Sisyphus/srpms/gnome-shell-extension-weather)

Install **gnome-shell-extension-weather** with apt-rpm from Sisyphus.

	sudo apt-get update
	sudo apt-get install gnome-shell-extension-weather

## Generic

Make sure you have these dependencies :

* `git`.
* `seed`.
* `libglib2.0-dev` : Without you'll get an error about `GLIB_GSETTINGS`.
* `gnome-common`.
* `gnome-tweak-tool`.

Run the following commands :

	cd ~ && git clone git://github.com/Neroth/gnome-shell-extension-weather.git
	cd ~/gnome-shell-extension-weather
	./autogen.sh --prefix=/usr && make && sudo make install

----

# Configuration

Use the `Weather Settings` button to edit the configuration.

**Always use this format when you add a city : "My City, My Country".**

Example : "New york, USA", "Paris, France", "Tokyo, Japan" ...

![Screenshot](https://github.com/neroth/gnome-shell-extension-weather/raw/master/data/weather-settings.gif)

You can also use `dconf-editor` or `gsettings` to modify some parameters from the command line :

#### City (`Cambridge, MA` (GNOME Foundation) by default)

You can specify your location using the following command. Perhaps you need quotation marks as in the second command.

    gsettings set org.gnome.shell.extensions.weather city your_city (for more : your_city && another_city && ...)
    gsettings set org.gnome.shell.extensions.weather city "your_city" (for more : your_city && another_city && ...)

#### Actual City (`0` by default)

You can specify the actual location using the following command.

    gsettings set org.gnome.shell.extensions.weather actual-city 0 ([your_city] && another_city && ...)
    gsettings set org.gnome.shell.extensions.weather actual-city 1 (your_city && [another_city] && ...)
    gsettings set org.gnome.shell.extensions.weather actual-city n (your_city && another_city && [...])

#### Temperature Units (optional, `celsius` by default)

You can modify the temperature unit using one of the following commands.

    gsettings set org.gnome.shell.extensions.weather unit celsius
    gsettings set org.gnome.shell.extensions.weather unit fahrenheit

#### Position in Panel (optional, `center` by default)

The position of this GNOME Shell extension in the panel can be configured to either 'left', 'center' or 'right' (requires restart of GNOME Shell).

    gsettings set org.gnome.shell.extensions.weather position-in-panel center
    gsettings set org.gnome.shell.extensions.weather position-in-panel left
    gsettings set org.gnome.shell.extensions.weather position-in-panel right

#### Translate Conditions (optional, `true` by default)

You may want to configure whether to translate the weather condition. If enabled, the condition is translated based on the weather code. If disabled, the condition string from Yahoo is taken. Note: Enabling the translation sometimes results in loss of accuracy, e.g., the condition string "PM Thunderstorms" cannot be expressed in terms of weather codes.

    gsettings set org.gnome.shell.extensions.weather translate-condition true
    gsettings set org.gnome.shell.extensions.weather translate-condition false

#### Symbolic Icons (optional, `true` by default)

If desired, you can enable the usage of full-colored icons to display the weather condition (instead of symbolic icons).

    gsettings set org.gnome.shell.extensions.weather use-symbolic-icons true
    gsettings set org.gnome.shell.extensions.weather use-symbolic-icons false

#### Temperature in Panel (optional, `true` by default)

You can configure whether to show the weather condition text (aka. comment) together with the temperature in the panel (requires restart). If only weather condition text is undesired, consider `Condition in Panel` option.

    gsettings set org.gnome.shell.extensions.weather show-text-in-panel true
    gsettings set org.gnome.shell.extensions.weather show-text-in-panel false

#### Condition in Panel (optional, `false` by default)

Configures whether to show the comment (aka. weather condition text, e.g. "Windy", "Clear") in the panel. Note that the temperature is still shown (if undesired, consider `Temperature in Panel` option).

    gsettings set org.gnome.shell.extensions.weather show-comment-in-panel false
    gsettings set org.gnome.shell.extensions.weather show-comment-in-panel true

#### Refresh Interval (optional, `300` by default)

The interval to refresh the weather information may be set arbitrarily and is specified in seconds.

    gsettings set org.gnome.shell.extensions.weather refresh-interval 300

#### Restart GNOME Shell

Don't forget to restart GNOME Shell (`[Alt]+[F2]`, `r`)

----

# Licence

Copyright (C) 2011 - 2012

* Christian METZLER <neroth@xeked.com>,
* Ecyrbe <ecyrbe+spam@gmail.com>,
* Timur Kristóf <venemo@msn.com>,
* Elad Alfassa <elad@fedoraproject.org>,
* Simon Legner <Simon.Legner@gmail.com>,
* Simon Claessens <gagalago@gmail.com>,
* Mark Benjamin <weather.gnome.Markie1@dfgh.net>

This file is part of gnome-shell-extension-weather.

gnome-shell-extension-weather is free software: you can redistribute it and/or modify it under the terms of the **GNU General Public License as published by the Free Software Foundation, either version 3** of the License, or (at your option) any later version.

gnome-shell-extension-weather is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with gnome-shell-extension-weather.  If not, see <http://www.gnu.org/licenses/>.
