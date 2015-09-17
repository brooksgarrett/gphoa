desc "clean"
task :clean do
  rm_rf '_site'
  FileList['**/*.bak'].clear_exclude.each do |f|
    rm_f f
  end
end

desc "build the site"
task :build do
  sh "bundle exec jekyll build"
end

desc "rebuild, then deploy to remote"
task :deploy => [ :clean, :build ] do
  sh "s3cmd sync _site/* s3://dev.brooksgarrett.com/"
end

desc "Default task is to clean and build"
task :default => [ :clean, :build ] do
  puts "Task complete"
end
