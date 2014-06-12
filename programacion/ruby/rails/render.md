http://guides.rubyonrails.org/layouts_and_rendering.html


Render ficheros .json:
render json: @tweet
render json: @zombie, status: :unprocessable_entity

Render ficheros .html.erb
render :otro <- otro.html.erb

Render un error y salir
render(:file => File.join(Rails.root, 'public/403.html'), :status => 403, :layout => false) and return

Render un partial (buscara el nombre con un guion bajo '_' delante del nombre)
<%= render 'parte' %>
<%= render 'host_group_field', f: builder %>

Render a una variable
script = render_to_string partial: 'script.sh.erb', locals: { project: @project, hostgroups: @hostgroups, vips: @vips }

Sin layout (donde suelen ir las cabeceras etc.)
La idea es sacar únicamente lo que tengamos en el .html.erb:
render layout: false