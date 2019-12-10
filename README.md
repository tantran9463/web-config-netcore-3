# when application net core 3 deployed on IIS, your APIs's method PUT can be method not allowed. So you must edit web.cfg to bellow.
# web-config

<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
	<modules>
	  <remove name="WebDAVModule" />
      <remove name="ApplicationInsightsWebTracking" />
      <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" preCondition="managedHandler" />
    </modules>
      <handlers>
	  <remove name="WebDAV" />
        <remove name="ExtensionlessUrlHandler-Integrated-4.0" />
        <remove name="OPTIONSVerbHandler" />
        <remove name="TRACEVerbHandler" />
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>      
    </system.webServer>
  </location>
</configuration>
