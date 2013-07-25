require './lib/evolution'

task :run do
  CONFIG = {
    :canvas_size => 200,
    :canvas_background => 'black',
    :render_directory => File.join(File.dirname(__FILE__), "/../images/renders"),
    :baseline_image => Magick::Image.read('./images/baselines/baseline-200.gif'),
    :add_polygon_mutation_rate => 100,
    :rgba_mutation_rate => 20,
    :point_mutation_rate => 20,
    :add_point_mutation_rate => 200
  }

  @most_fit = Evolution::Candidate.new

  while @most_fit.fitness > 10
    child = @most_fit.spawn_child
    write = 0

    if child.fitness < @most_fit.fitness
      write += 1
      child.save if write % 50 == 0
      puts child.to_s
      @most_fit = child
    end
  end
end
