#===[ Configuration ]===================================================

host = 'opensourcebridge.org'
path = '/var/www/bridgepdx_wiki/skins'

#===[ Tasks ]===========================================================

task :default => :deploy

desc "Deploys common style files using rsync"
task :deploy do
  sh "rsync -uvax --progress --delete --exclude=.* --exclude=Rakefile ./ #{host}:#{path}"
end

desc "Symlink this skin into a copy of MediaWiki at DIR"
task :link do
  unless mediawiki_dir = ENV['DIR']
    puts <<-EOB
ERROR: You must specify a MediaWiki directory with DIR to link into, e.g.,:
  rake link DIR=../bridgepdx_wiki
    EOB
    exit 1
  end

  source_file = 'OSBridge.php'
  source_dir = 'osbridge'
  target_file = File.expand_path(File.join(mediawiki_dir, 'skins', source_file))
  target_dir = File.expand_path(File.join(mediawiki_dir, 'skins', source_dir))

  rm target_file if File.exist?(target_file)
  rm_r target_dir if File.exist?(target_dir)

  ln_sf File.expand_path(source_file), target_file
  ln_sf File.expand_path(source_dir), target_dir
end
task :symlink => :link # Alias

#===[ fin ]=============================================================
