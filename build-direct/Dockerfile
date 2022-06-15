# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <https://www.gnu.org/licenses/>.

#LABEL org.opencontainers.image.source="https://github.com/speedy-beaver/calibre-downloader"
FROM ubuntu:focal
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive TZ=Europe/Stockholm apt-get -y install tzdata
RUN apt-get -y install wget sudo python3 xz-utils libgl1-mesa-dev libxcb-cursor0 libnss3
RUN sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin

ENV RECIPE "The Economist"
ENV FORMAT "epub"
ENV OUTPUTPROFILE "kindle"

VOLUME /tmp/calibre

CMD ["bash","-c","ebook-convert \"${RECIPE}\".recipe /tmp/calibre/\"${RECIPE}\".${FORMAT} --output-profile ${OUTPUTPROFILE}"]
