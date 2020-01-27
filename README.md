# elasticsearch
Setting ElasticSearch with MSSQL

(for some reason github is not allow large file to be upload - read lfs here to do it https://git-lfs.github.com/ )
![image](https://user-images.githubusercontent.com/36264533/73153163-49fa3e00-4105-11ea-9e3b-15d58962e51b.png)

<ol>
<li><strong>Download and install those files</strong>
    <p>Basically, ES is very easy to config. Just focus to config file (<em>/config/elasticsearch.yml</em>) and batch (<em>/bin/elasticsearch.bat</em>)&nbsp;</p>
  <p>Moditify <strong>elasticsearch.bat&nbsp;</strong>with those config</p>
  `
  <p>@echo off@echo off<br />setlocal enabledelayedexpansionsetlocal enableextensions<br />SET params='%*'<br />:loopFOR /F "usebackq tokens=1* delims= " %%A IN (!params!) DO (&nbsp; &nbsp; SET current=%%A&nbsp; &nbsp; SET params='%%B' SET silent=N<br /> IF "!current!" == "-s" ( SET silent=Y ) IF "!current!" == "--silent" ( SET silent=Y )<br /> IF "!silent!" == "Y" ( SET nopauseonerror=Y ) ELSE ( &nbsp; &nbsp; IF "x!newparams!" NEQ "x" ( &nbsp; &nbsp; &nbsp; &nbsp; SET newparams=!newparams! !current!&nbsp; &nbsp; &nbsp; &nbsp; ) ELSE (&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SET newparams=!current!&nbsp; &nbsp; &nbsp; &nbsp; ) )<br />&nbsp; &nbsp; IF "x!params!" NEQ "x" ( GOTO loop ))<br />CALL "%~dp0elasticsearch-env.bat" || exit /b 1IF ERRORLEVEL 1 ( IF NOT DEFINED nopauseonerror ( PAUSE ) EXIT /B %ERRORLEVEL%)<br />if not defined ES_TMPDIR (&nbsp; for /f "tokens=* usebackq" %%a in (`CALL %JAVA% -cp "!ES_CLASSPATH!" "org.elasticsearch.tools.launchers.TempDirectory"`) do set&nbsp; ES_TMPDIR=%%a)<br />set ES_JVM_OPTIONS=%ES_PATH_CONF%\jvm.options@setlocalfor /F "usebackq delims=" %%a in (`CALL %JAVA% -cp "!ES_CLASSPATH!" "org.elasticsearch.tools.launchers.JvmOptionsParser" "!ES_JVM_OPTIONS!" ^|^| echo jvm_options_parser_failed`) do set JVM_OPTIONS=%%a@endlocal &amp; set "MAYBE_JVM_OPTIONS_PARSER_FAILED=%JVM_OPTIONS%" &amp; set ES_JAVA_OPTS=%JVM_OPTIONS:${ES_TMPDIR}=!ES_TMPDIR!%<br />if "%MAYBE_JVM_OPTIONS_PARSER_FAILED%" == "jvm_options_parser_failed" (&nbsp; exit /b 1)<br />%JAVA% %ES_JAVA_OPTS% -Delasticsearch -Des.path.home="%ES_HOME%" -Des.path.conf="%ES_HOME%"/config -Des.distribution.flavor="%ES_DISTRIBUTION_FLAVOR%" -Des.distribution.type="%ES_DISTRIBUTION_TYPE%" -Des.bundled_jdk="%ES_BUNDLED_JDK%" -cp "%ES_CLASSPATH%" "org.elasticsearch.bootstrap.Elasticsearch" !newparams!<br />endlocalendlocalexit /b %ERRORLEVEL%</p>
  `
</li>
<li><strong>Setup Elasticsearch</strong></li>
<li><strong>Setup Logstash</strong></li>
<li><strong>Setup Kibana</strong></li>
</ol>
