require 'open3'
task :template do

  command = <<COMANDO
pandoc -f markdown -t latex -s
--data-dir=.
--smart
--normalize
--template=trabalho-academico-abnt
-o target/monografia.tex
--chapters
COMANDO

  text = `cat trabalho-academico.md siglas.yaml`
  text = text.gsub!('°','º').gsub!('²','^2^')

  puts command.gsub!(/\n/,' ')

  Open3.popen3(command) {|stdin, stdout, stderr, wait_thr|
    stdin.write text
    stdin.close
    puts stdout.read
    puts stderr.read
  }

  Dir.chdir('target') do
    system "pdflatex monografia"
    system "pdflatex monografia"
  end

end

task :default => :template

task :text do

  text
  puts text

end
