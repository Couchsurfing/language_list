require 'bundler'
Bundler::GemHelper.install_tasks

require 'rake/testtask'
Rake::TestTask.new do |t|
  t.test_files = FileList['test/language_list_test.rb']
  t.verbose = true
end

task :default => :test

desc 'Rebuilds Marshal dump file.'
task :rebuild_dump do
  require 'yaml'
  require_relative 'lib/language_list'
  puts 'Rebuilding dump from data/languages.yml'
  yml_data = YAML.load_file('data/languages.yml')
  langs = yml_data.map { |item| LanguageList::LanguageInfo.new(item) }
  langs_dump = Marshal.dump(langs)
  File.open('data/dump', 'wb') { |f| f.write(langs_dump)}
  puts 'Finished.'
end
