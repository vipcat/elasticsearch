# elasticsearch
Setting ElasticSearch with MSSQL

(for some reason github is not allow large file to be upload - read lfs here to do it https://git-lfs.github.com/ )
![image](https://user-images.githubusercontent.com/36264533/73153163-49fa3e00-4105-11ea-9e3b-15d58962e51b.png)

<ol>
<li><strong>Download and install those files</strong>
  <p><a href="https://github.com/vipcat/elasticsearch/blob/master/jre-8u231-windows-x64.rar">Java8 Installer</a></p>
  <p><a href="https://github.com/vipcat/elasticsearch/blob/master/ElasticSearch.rar">ES PACKAGE</a></p>
  Keep ur mind with some Environment config 
  ![image](https://user-images.githubusercontent.com/36264533/73154815-36ea6c80-410b-11ea-8f67-136dae29d90b.png)
  ![image](https://user-images.githubusercontent.com/36264533/73153163-49fa3e00-4105-11ea-9e3b-15d58962e51b.png)
</li>
<li><strong>Setup Elasticsearch</strong>
  <p>Basically, ES is very easy to config. Just focus to config file (<strong><em>/config/elasticsearch.yml</em></strong>) and batch (<strong><em>/</em>bin/elasticsearch.bat</strong>)&nbsp;</p>
<p>Moditify <strong>elasticsearch.bat&nbsp;</strong>with those config</p>
<p><a href="https://github.com/vipcat/elasticsearch/blob/master/elasticsearch.bat">https://github.com/vipcat/elasticsearch/blob/master/elasticsearch.bat</a></p>
<p>With this config es will know your config file located in <em>/config/elasticsearch.yml&nbsp;</em>( nvm it if you need it run in default java configuration. )</p>
<p>Well, now&nbsp; just go to the bin folder and run this batch file.</p>
<p><span style="text-decoration: underline;"><strong>Config detail</strong></span></p>
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
<li><strong>Setup Logstash</strong></li>
<li><strong>Setup Kibana</strong></li>
</ol>
