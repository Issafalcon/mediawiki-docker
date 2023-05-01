FROM mediawiki:1.39

RUN chmod a+x /var/www/html/extensions/Scribunto/includes/engines/LuaStandalone/binaries/lua*_linux_*/lua

# Install BetaFeatures extension
# See https://www.mediawiki.org/wiki/Extension:BetaFeatures
RUN curl -Ls https://extdist.wmflabs.org/dist/extensions/BetaFeatures-REL1_39-b5ac551.tar.gz | tar -xzC /var/www/html/extensions

# RUN git clone --depth 1 -b $MEDIAWIKI_BRANCH \
#   https://gerrit.wikimedia.org/r/mediawiki/extensions/MobileFrontend \
#   /var/www/html/extensions/MobileFrontend
#
RUN git clone --depth 1 https://github.com/StarCitizenTools/mediawiki-skins-Citizen.git /var/www/html/skins/Citizen
