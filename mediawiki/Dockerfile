FROM mediawiki:1.39

RUN chmod a+x /var/www/html/extensions/Scribunto/includes/engines/LuaStandalone/binaries/lua*_linux_*/lua \
  # Allow web server user to upload files to images folder (required for mediawiki uploads to wok)
  && chown www-data /var/www/html/images

# Required for VisualEditor on 32bit machines
RUN docker-php-ext-install bcmath

# Install BetaFeatures extension
# See https://www.mediawiki.org/wiki/Extension:BetaFeatures
RUN curl -Ls https://extdist.wmflabs.org/dist/extensions/BetaFeatures-REL1_39-ef1b140.tar.gz | tar -xzC /var/www/html/extensions

# RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
#   https://gerrit.wikimedia.org/r/mediawiki/extensions/MobileFrontend \
#   /var/www/html/extensions/MobileFrontend
#
RUN git clone --depth 1 https://github.com/StarCitizenTools/mediawiki-skins-Citizen.git /var/www/html/skins/Citizen

# Install Math extension
RUN curl -Ls https://extdist.wmflabs.org/dist/extensions/Math-REL1_39-b1514e1.tar.gz | tar -xzC /var/www/html/extensions

# Install PDFEmbed extension
RUN curl -Ls https://github.com/WolfgangFahl/PDFEmbed/archive/refs/tags/3.0.1.tar.gz | tar -xzC /var/www/html/extensions

# Apt update and install required packages for Mathoid https://www.mediawiki.org/wiki/Manual:Mathoid
RUN apt-get update && apt-get install -y \
  nodejs \
  npm \
  librsvg2-dev \
  pkg-config \ 
  g++

RUN git clone https://gitlab.wikimedia.org/repos/mediawiki/services/mathoid /var/data/wiki/mathoid

# Change to mathoid directory
WORKDIR /var/data/wiki/mathoid
RUN npm install
RUN cp config.prod.yaml config.yaml
