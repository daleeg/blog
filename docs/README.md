## Welcome to GitHub Pages

[https://daleeg.github.io/blog/](https://daleeg.github.io/blog/)

You can use the [editor on GitHub](https://github.com/vallee11/blog/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Rabbitmq cluster
## 1. 安装 (ubuntu)

	apt install erlang -y
	apt install erlang-nox -y
	apt-get install rabbitmq-server -y
	rabbitmq-plugins enable rabbitmq_management

## 2. 配置

### 1. /etc/rabbitmq/rabbitmq-env.conf

	NODENAME=rabbit-153
	NODE_IP_ADDRESS=10.88.190.153
	CONFIG_FILE=/etc/rabbitmq/rabbitmq
	HOME=/var/lib/rabbitmq

### 2. /var/lib/rabbitmq/.erlang.cookie

    #所有机器
    fsdfsdfdsfsdfsdfsdf

### 3. /etc/hosts
	#所有机器
	10.88.190.153 master
	10.88.190.154 slave1
	10.88.190.155 slave2

### 4. /etc/rabbitmq/rabbitmq.config
	
	[
    {rabbit, [
    {cluster_nodes, {['10.88.190.153@master'], disc}},
    {cluster_partition_handling, ignore},
    {default_user, <<"admin">>},
    {default_pass, <<"admin">>},
    {tcp_listen_options, [binary,
        {packet, raw},
        {reuseaddr, true},
        {backlog, 128},
        {nodelay, true},
        {exit_on_close, false},
        {keepalive, true}]}
    ]},
    {kernel, [
        {inet_dist_listen_max, 44001},
        {inet_dist_listen_min, 44001}
    ]}
].


## 3. 部署

###1. 主机153
   	service rabbitmq-server restart

###2. 主机154
   	service rabbitmq-server restart
    rabbitmqctl stop_app
	rabbitmqctl join_cluster --ram rabbit_153@master
	rabbitmqctl start_app

###3. 主机155
   	service rabbitmq-server restart
    rabbitmqctl stop_app
	rabbitmqctl join_cluster --ram rabbit_153@master
	rabbitmqctl start_app

## 4. 常用命令
	rabbitmqctl stop_app
	
	rabbitmqctl change_cluster_node_type dist
	
	rabbitmqctl change_cluster_node_type ram
	
	rabbitmqctl start_app

	/usr/sbin/rabbitmqctl add_user rabbit rabbit

    /usr/sbin/rabbitmqctl set_user_tags rabbit management 

    /usr/sbin/rabbitmqctl add_vhost rabbit 

    /usr/sbin/rabbitmqctl set_permissions -p rabbit rabbit '.*' '.*' '.*' 



- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/vallee11/blog/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
