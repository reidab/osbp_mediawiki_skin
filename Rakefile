#===[ Configuration ]===================================================

host = 'opensourcebridge.org'
path = '/var/www/bridgepdx_wiki/skins'

#===[ Tasks ]===========================================================

task :default => :deploy

desc "Deploys common style files using rsync"
task :deploy do
  sh "rsync -uvax --progress --delete --exclude=.* --exclude=Rakefile ./ #{host}:#{path}"
end

#===[ fin ]=============================================================
