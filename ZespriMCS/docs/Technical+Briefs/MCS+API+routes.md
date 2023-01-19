# **MCS API routes**
The APIs in MCS are split between two function apps:

- azfun-zes-prd-wu2-external-packhouse (next.js)
- azfun-zes-prd-wu2-internal-orchard-master-data (C#)

The names of the function apps aren’t 100% accurate now since we have built both “internal” and “external” APIs in the Next.js function app. 

All APIs are accessed through API Manager for security and scalability. 

API URLs are as follows: {API-URL}

- PROD: https://api.zespri.com/
- Other environments: https://api-{ENV}.zespri.com - where {ENV} is PPE, TST or DEV

Both function apps have different base routes in API Manager {base route}

- /internal = all C# APIs 
- /mcs = all Next.js APIs

Full API Path is then:

{API-URL}(base route)(API route)

eg: 

https://api.zespri.com/mcs/admin/clearance-criteria

https://api.zespri.com/internal/sas/generate

|**Repo**|**Build pipeline(s)**|**Release pipeline**|**Deployment**|
| :-: | :-: | :-: | :-: |
|<p>Zespri.MCS.UI</p><p>Next.js APIs</p>|MCS-External API next.js|MCS-External API-NextJs|azfun-zes-prd-wu2-external-packhouse|
|/admin/clearance-criteria/groups<br>/admin/clearance-criteria/groups/toggle-active-version<br>/admin/clearance-criteria<br>/admin/clearance-criteria/options<br>/admin/clearance-criteria/rules<br>/admin/clearance-criteria/rules/update-next-active<br>/admin/test-group<br>/admin/test-group/sample-count<br>/admin/test-group/update-status<br>/admin/test-groups<br>/admin/test-groups/options<br>/admin/test-groups/sample-types<br>/areas/checker<br>/areas<br>/associations<br>/auth/callback<br>/auth/request-impersonation-token<br>/auth/request-token<br>/auth/validate-token<br>/authz/requestToken<br>/authz/validateToken<br>/blocks-year-producing<br>/cancel-reasons<br>/change-packhouse-user<br>/clearance-criteria-override<br>/collection-date<br>/current-season<br>/download/block-association<br>/download/hazards<br>/download/orchard-info<br>/download/sample/fruit-level-data<br>/download/sample/info<br>/download/sample/results<br>/duplicate-area<br>/duplicate-request<br>/email/send<br>/file<br>/filters<br>/incoming-measures<br>/kpin-list<br>/ma-dispensation-rules<br>/ma-notifications<br>/maps/[id]<br>/maps<br>/orchard/hazard<br>/orchards/[kpin]/flag<br>/orchards/[kpin]/hazards/[id]<br>/orchards/[kpin]/hazards/verify<br>/orchards/[kpin]<br>/orchards/[kpin]/info<br>/orchards/[kpin]/part-blocks/[blockId]<br>/orchards/[kpin]/part-blocks<br>/orchards<br>/packhouses-options<br>/packhouses/[id]<br>/powerbi/auth<br>/powerbi/embed-token<br>/powerbi/reports<br>/release<br>/reports/graphs<br>/reports/tables<br>/reports/industry-summary<br>/reports/industry-trend/graphs<br>/reports/industry-trend/tables<br>/roles/[id]<br>/roles<br>/sample-request<br>/sample-request/release-comments<br>/sample-request/zero-rates<br>/samplerequests<br>/samplerequests/tooltips/colour<br>/samplerequests/tooltips/inherited-sample<br>/samplerequests/tooltips/kpin<br>/samplerequests/tooltips/release<br>/samplerequests/tooltips/service-providers<br>/samplerequests/tooltips/status<br>/samplerequests/validation/area-sample-processing<br>/samplerequests/validation/one-clearance-request-per-day<br>/samplerequests/validation/one-residue-request-at-a-time<br>/samplerequestsfilters<br>/send/notification<br>/site-requirements/[kpin]<br>/sr-companies<br>/terms<br>/test-results<br>/update-criteria<br>/update-status<br>/users/[id]<br>/users||||
|<p>Zespri.MCS.APIs</p><p>C# APIs</p>|MCS-Orchard API|MCS-Orchard API |azfun-zes-prd-wu2-internal-orchard-master-data|
|/areas (not used - works on /areas UI?)<br>/areas/upload<br>/filters (moved to Next.js repo)<br>/maps<br>/maps/{mapId}<br>/orchards<br>/orchards/{kpin}<br>/orchards/{kpin}/areas<br>/orchards/{kpin}/areas/{areaId}<br>/orchards/{kpin}/hazards<br>/orchards/{kpin}/hazards/{id}<br>/orchards/{kpin}/part-blocks<br>/orchards/{kpin}/part-blocks/{blockId}<br>/orchards/blockassociations/upload<br>/orchards/hazards/upload<br>/orchards/siterequirements/upload<br>/samplerequestfilters (moved to Next.js repo)<br>/samplerequests<br>/samplerequests/{sampleId}<br>/samplerequests/associations<br>/samplerequests/associations/{sampleId}<br>/samplerequests/releases<br>/samplerequests/results<br>/samplerequests/state<br>/samplerequests/upload<br>/sas/generate<br>/siterequirements/{kpin} (moved to Next.js repo)||||

