# elasticsearch
Setting ElasticSearch with MSSQL

(for some reasons github is not allow large file to be uploaded - read lfs here to do it https://git-lfs.github.com/ )
![image](https://user-images.githubusercontent.com/36264533/73153163-49fa3e00-4105-11ea-9e3b-15d58962e51b.png)

1. [Config Unicode folding ( bỏ dấu tiếng Việt )](#unicode-folding)
2. [Config Vietnamese Analyser ( tách cụm từ tiếng Việt)](#vietnamese-analyser)
3. [Reindex ES Instance](#reindex)
4. [Node Client](#node-client)

<ol>
<li><strong>Download and install those files</strong>
  <p><a href="https://github.com/vipcat/elasticsearch/blob/master/jre-8u231-windows-x64.rar">Java8 Installer</a></p>
  <p><a href="https://github.com/vipcat/elasticsearch/blob/master/ElasticSearch.rar">ES PACKAGE</a></p>
  Keep ur mind in some Environment configs 
  <p><img src="https://user-images.githubusercontent.com/36264533/73154815-36ea6c80-410b-11ea-8f67-136dae29d90b.png" alt="" width="600" height="400" /></p>
</li>
<li><strong>Setup Elasticsearch</strong>
  <p>Basically, ES is very easy to config. Just focus to config file (<strong><em>/config/elasticsearch.yml</em></strong>) and batch (<strong><em>/</em>bin/elasticsearch.bat</strong>)&nbsp;</p>
<p>Moditify <strong>elasticsearch.bat&nbsp;</strong>with those config</p>
<p><a href="https://github.com/vipcat/elasticsearch/blob/master/elasticsearch.bat">https://github.com/vipcat/elasticsearch/blob/master/elasticsearch.bat</a></p>
<p>With this config es will know your config file located in <em>/config/elasticsearch.yml&nbsp;</em>( nvm it if you need it run in default java configuration. )</p>
<p>Well, now&nbsp; just go to the bin folder and run this batch file.</p>
<p><span style="text-decoration: underline;"><strong>Config details</strong></span></p>
<table>
<tbody>
<tr>
<td>
<div>
<div>http.port:&nbsp;9400</div>
</div>
</td>
<td>&nbsp;Port&nbsp;</td>
</tr>
<tr>
<td>
<div>
<div>transport.tcp.port:&nbsp;9500</div>
</div>
</td>
<td>&nbsp;Transport port</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>discovery.seed_hosts&nbsp;:&nbsp;0.0.0.0</div>
</div>
</div>
</div>
</td>
<td>&nbsp;Config wan IP</td>
</tr>
<tr>
<td>
<div>
<div>
<div>
<div>
<div>
<div>network.host:&nbsp;0.0.0.0</div>
</div>
</div>
</div>
</div>
</div>
</td>
<td>&nbsp;Config wan IP</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
</li>
<li><strong>Setup Logstash</strong>
  <p><strong>Logstash&nbsp;</strong>is the way to push data from Database to your ES Instance.</p>
<p><strong>Basic config&nbsp;</strong></p>
<p><a href=" https://github.com/vipcat/elasticsearch/blob/master/logstash-config.conf"> https://github.com/vipcat/elasticsearch/blob/master/logstash-config.conf</a></p>
<table>
<tbody>
<tr>
<td>jdbc_connection_string =&gt; "jdbc:sqlserver://xxx;database=xxx;integratedSecurity=false;"</td>
<td>Conntection string to your database</td>
</tr>
<tr>
<td>jdbc_driver_class =&gt; "com.microsoft.sqlserver.jdbc.SQLServerDriver"</td>
<td>just keep it</td>
</tr>
<tr>
<td>jdbc_driver_library =&gt; "C:\sqljdbc42.jar"</td>
<td>sqljdbc located ( include in package )</td>
</tr>
<tr>
<td>statement =&gt; "SELECT * email from Users"</td>
<td>yep, sql query</td>
</tr>
<tr>
<td>hosts =&gt; ["localhost:9400"]</td>
<td>ES instance url</td>
</tr>
<tr>
<td>index =&gt; "xx"</td>
<td>ES instance index name</td>
</tr>
</tbody>
</table>
<p>Go to logstash bin folder then run this command</p>
<p><strong><em>logstash -f logstash-config.conf</em></strong></p>
<p><strong>Here you go !</strong></p>
<p>Navigate to <a href="http://localhost:9400/_search?q=xxxxx">http://localhost:9400/_search?q=xxxxx</a>&nbsp;and enjoy it ( ;v only if it works )</p>
<p>Some more configuration will be explained in the next few days</p>
  <p>&nbsp;</p>
</li>

<li><strong>Setup Kibana</strong>
<p><strong>Kibana&nbsp;</strong>is the way to see data :D&nbsp;</p>
<p>Go to kibana bin folder then run this command&nbsp;</p>
<p><strong>kibana -e <a href="http://localhost:9400">http://localhost:9400</a>&nbsp;-p 5061</strong></p>
<table>
<tbody>
<tr>
<td>-e</td>
<td>host address</td>
</tr>
<tr>
<td>-p</td>
<td>custom port</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
</li>
</ol>

#### Unicode folding
`update`

#### Vietnamese Analyser
`update`

#### Reindex
`update`

#### Node Client
`update`
