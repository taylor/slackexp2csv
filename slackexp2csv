require 'json'
require 'fastercsv'

if ARGV.length < 1
  puts "usage: slackexp2csv.rb <slack export dir>"
  exit 1;
end

expdir=ARGV[0]

if not File.exists?(expdir) 
  puts "Directory #{expdir} does not exist!"
  exit 1;
elsif not File.exists?(File.join(expdir, 'channels.json'))
  puts "Directory #{expdir} does not seem to be a valid slack.com data export"
  exit 1;
end

jchannels=JSON.parse(IO.read(File.join(expdir, 'channels.json')))
jusers=JSON.parse(IO.read(File.join(expdir, 'users.json')))
channeldirs=Dir.glob("#{expdir}/*/").collect {|d| File.basename(d)}

users = Hash.new
jusers.collect {|u| users[u['id']] = u['name'] }

channeldirs.each do |c|
  messagefiles = Dir.glob("#{File.join(expdir, c)}/*.json")
  messagefiles.each do |mf|
    jmsg = JSON.parse(IO.read(File.join(mf)))
    jmsg.each do |m|
      puts "#{m['ts']},#{c},#{users[m['user']]},#{m['text']}"
    end
  end
end


