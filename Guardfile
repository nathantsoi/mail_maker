
# Sample guardfile block for Guard::Haml
# You can use some options to change guard-haml configuration
# :output => 'public'                   set output directory for compiled files
# :input => 'src'                       set input directory with haml files
# :run_at_start => true                 compile files when guard starts
# :notifications => true                send notifictions to Growl/libnotify/Notifu
# :haml_options => { :ugly => true }    pass options to the Haml engine

guard 'haml' do
  watch(/^.+(\.html\.haml)/)
end

def compile_mail file
  require 'premailer'
  premailer = ::Premailer.new(file, :warn_level => Premailer::Warnings::SAFE)
  html_out = file.split('.', -1).join('.premailer.')
  txt_out = file.split('.', -1).first + '.txt'

  # Write the HTML output
  fout = File.open(html_out, "w")
  fout.puts premailer.to_inline_css
  fout.close

  # Write the plain-text output
  fout = File.open(txt_out, "w")
  fout.puts premailer.to_plain_text
  fout.close

  # Output any CSS warnings
  premailer.warnings.each do |w|
    puts "#{w[:message]} (#{w[:level]}) may not render properly in #{w[:clients]}"
  end
end

guard :shell do
  watch(/^.+(?<!\.premailer)\.html$/) do |m|
    m.each{|file| compile_mail file }
  end
end

guard 'livereload' do
  watch(%r{.+\.(erb|haml|slim)$})
end
