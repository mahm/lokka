require 'init'


desc 'Create the Pyha database'
task 'db:migrate' do
  DataMapper.auto_migrate!
end

desc 'Execute seed script'
task 'db:seed' do
  # user
  User.create(:name => 'komagata', :password => 'test', :password_confirmation => 'test')
  User.create(:name => 'test1', :password => 'test', :password_confirmation => 'test')

  # site
  Site.create(:name => 'title', :value => 'Test Site')
  Site.create(:name => 'description', :value => 'description...')
  Site.create(:name => 'theme', :value => 'vicuna-mono')

  # post
  (1..11).each do |i|
    Post.create(
      :user_id     => 1,
      :category_id => 1,
      :title       => "Test Post ... #{i}",
      :body        => "body ... #{i}",
      :slug        => "slug-#{i}"
    )
  end

  # page
  (12..20).each do |i|
    Page.create(
      :user_id     => 1,
      :category_id => 1,
      :title       => "Test Page ... #{i}",
      :body        => "body ... #{i}",
      :slug        => "slug-#{i}"
    )
  end

  # category
  Category.create(:name => 'Category 1', :slug => 'slug-1')
  Category.create(:name => 'Category 2', :slug => 'slug-2')
  Category.create(:name => 'Category 3', :slug => 'slug-3')
  Category.create(:name => 'Category 4', :slug => 'slug-4', :parent_id => 1)
  Category.create(:name => 'Category 5', :slug => 'slug-5', :parent_id => 1)
end

desc 'Reset database'
task 'db:reset' => %w(db:migrate db:seed)

desc 'Bundler'
task :bundle do
  `bundle install --without production`
end

desc 'Rebundler'
task :rebundle do
  `bundle install --without production`
end

desc 'Install'
task :install => %w(bundle db:reset)

desc 'Reinstall'
task :reinstall => %w(rebundle db:reset)
