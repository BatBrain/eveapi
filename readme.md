EVE staic data from https://developers.eveonline.com/resource/resources
EVE market transaction history from: https://eve-central.com/dumps/

For transation history download and updates use this in command line (linux only, must have GNU parallel and lynx installed):

rm -rf links.txt; lynx -dump "https://eve-central/dumps/" | egrep -o "https://eve-central/dumps/.2016*(dump.gz)" > links.txt; cat links.txt | parallel -j10 "wget -Ncv {}";

you can change the year you want by changing the year in the command, or removing it for all years (good luck with that, it will take a LONG while if you do) also, you can change the wget section to pull from multiple connections for each file, but I would advise against that as you could end up choking eve-central's bandwidth.
