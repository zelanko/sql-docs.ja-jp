---
title: "SoapException エラー テーブル |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SoapException class
ms.assetid: 3dbf1b5a-bd2a-4385-925d-5d095d72014c
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6261b3b96ab564e9852c30bf5bac139cf924da60
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="soapexception-errors-table"></a>SoapException エラー テーブル
  レポート サーバーでは、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] で発生するエラーに基づいて、SOAP 例外のエラーとエラー メッセージが生成されます。 次の表に、使用してメソッドからアクセス可能であるエラー、 **SoapException**レポート サーバー Web サービスにします。 例外をスローする 1 つまたは複数のメソッド別に分類されています。  
  
|メソッド|エラー コード|  
|-----------------|----------------|  
|**ALL**|**rsEvaluationCopyExpired**|  
|**ALL**|**rsFailedToDecryptConfigInformation**|  
|**ALL**|**rsInvalidRSEditionConfiguration**|  
|**ALL**|**rsReportServerNotActivated**|  
|**ALL**|**rsServerBusy**|  
|**ALL**|**rsReportServerServiceUnavailable**|  
|**ALL**|**rsReportServerDisabled**|  
|**すべて**を除く**GetPermissions**、 **GetRenderResource**、 **GetSystemPermissions**、 **ListEvents**、および**すべてのメソッド**|**rsAccessDenied**|  
|**すべて**を除く**CreateBatch**、 **ExecuteBatch**、 **GetSystemPolicies**、 **GetSystemPermissions**、 **GetSystemProperties**、 **ListEvents**、 **ListJobs**、 **ListRoles**、 **ListSchedules**、**すべてのメソッド**、 **ListSubscriptions**、 **ListSystemRoles**、 **ListSystemTasks**、 **ListTasks**|**rsMissingParameter**|  
|**CreateDataDrivenSubscription**、 **CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateReportHistorySnapshot**、 **CreateResource**、 **CreateSubscription**、 **DeleteItem**、 **DeleteReportHistorySnapshot**、 **DisableDataSource**、 **EnableDataSource**、 **FindItems**、 **FlushCache**、 **GetCacheOptions**、 **GetDataSourceContents**、 **GetExecutionOptions**、 **GetPermissions**、 **GetPolicies**、 **GetProperties**、 **GetReportDataSourcePrompts**、 **GetReportDataSources**、 **GetReportDefinition**、 **GetReportHistoryLimit**、 **GetReportHistoryOptions**、 **GetReportLink**、 **GetReportParameters**、 **GetResourceContents**、 **GetRoleProperties**、 **GetServerDateTime**、 **IheritParentSecurity**、 **ListChildren**、 **ListLinkedReports**、 **ListReportHistory**、 **ListReportsUsingDataSource**、 **ListSchedules**、 **ListSubscriptions**、 **ListSubscriptionsUsingDataSource**、 **MoveItem**、**レンダリング**、 **RenderStream**、 **SetCacheOptions**、 **SetDataSourceContents**、 **SetExecutionOptions**、 **SetPolicies**、 **SetProperties**、 **SetReportDataSources**、 **SetReportDefinition**、 **SetReportHistoryLimit**、 **SetReportHistoryOptions**、 **SetReportLink**、 **SetReportParameters**、 **SetResourceContents**、 **UpdateReportExecutionSnapshot**、 **ValidateExtensionSettings**|**rsItemNotFound**|  
|**CancelBatch**、 **CreateDataDrivenSubscription**、 **CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateReportHistorySnapshot**、 **CreateResource**、 **CreateRole**、 **CreateSchedule**、 **CreateSubscription**、 **DeleteItem**、 **DeleteReportHistorySnapshot**、 **DeleteRole**、 **DeleteSchedule**、 **DeleteSubscription**、 **DisableDataSource**、 **EnableDataSource**、 **ExecuteBatch**、 **FindItems**、 **FlushCache**、 **GetResourceContents**、 **GetServerDateTime**、 **MoveItem**、 **PauseSchedule**、 **ResumeSchedule**、 **SetCacheOptions**、 **SetDataDrivenSubscriptionProperties**、 **SetDataSourceContents**、 **SetExecutionOptions**、 **SetPolicies**、 **SetProperties**、 **SetReportDataSources**、 **SetReportDefinition**、 **SetReportHistoryLimit**、 **SetReportHistoryOptions**、 **SetReportLink**、 **SetReportParameters**、 **SetResourceContents**、 **SetRoleProperties**、 **SetScheduleProperties**、 **SetSubscriptionProperties**、 **SetSystemPolicies**、 **SetSystemProperties**、 **UpdateReportExecutionSnapshot**、 **ValidateExtensionSettings**|**rsBatchNotFound**|  
|**CreateDataDrivenSubscription**、 **CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateReportHistorySnapshot**、 **CreateResource**、 **CreateSubscription**、 **DeleteItem**、 **DeleteReportHistorySnapshot**、 **DisableDataSource**、 **EnableDataSource**、 **FindItems**、 **FlushCache**、 **GetCacheOptions**、 **GetDataSourceContents**、 **GetExecutionOptions**、 **GetItemType**、 **GetPermissions**、 **GetPolicies**、 **GetProperties**、 **GetReportDataSourcePrompts**、 **GetReportDataSources**、 **GetReportDefinition**、 **GetReportHistoryLimit**、 **GetReportHistoryOptions**、 **GetReportLink**、 **GetResourceContents**、 **GetServerDateTime**、 **IheritParentSecurity**、 **ListChildren**、 **ListLinkedReports**、 **ListReportHistory**、 **ListSchedules**、 **ListSubscriptionsUsingDataSource**、 **MoveItem**、**レンダリング**、 **RenderStream**、 **SetCacheOptions**、 **SetDataSourceContents**、 **SetExecutionOptions**、 **SetPolicies**、 **SetProperties**、 **SetReportDataSources**、 **SetReportDefinition**、 **SetReportHistoryLimit**、 **SetReportHistoryOptions**、 **SetReportLink**、 **SetReportParameters**、 **SetResourceContents**、 **SetSubscriptionProperties**、 **UpdateReportExecutionSnapshot**、 **ValidateExtensionSettings**|**rsInvalidItemPath**|  
|**CreateDataDrivenSubscription**、 **CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateReportHistorySnapshot**、 **CreateResource**、 **CreateSubscription**、 **DeleteReportHistorySnapshot**、 **DisableDataSource**、 **EnableDataSource**、 **FindItems**、 **FlushCache**、 **GetCacheOptions**、 **GetDataSourceContents**、 **GetExecutionOptions**、 **GetReportDataSourcePrompts**、 **GetReportDataSources**、 **GetReportDefinition**、 **GetReportHistoryLimit**、 **GetReportHistoryOptions**、 **GetReportLink**、 **GetReportParameters**、 **GetResourceContents**、 **GetServerDateTime**、 **GetSystemProperties**、 **ListChildren**、 **ListLinkedReports**、 **ListReportHistory**、 **ListReportsUsingDataSource**、 **ListSchedules**、 **ListSubscriptions**、 **ListSubscriptionsUsingDataSource**、 **MoveItem**、**レンダリング**、 **RenderStream**、 **SetCacheOptions**、 **SetDataSourceContents**、 **SetExecutionOptions**、 **SetReportDataSources**、 **SetReportDefinition**、 **SetReportHistoryLimit**、 **SetReportHistoryOptions**、 **SetReportLink**、 **SetReportParameters**、 **SetResourceContents**、 **UpdateReportExecutionSnapshot**、 **ValidateExtensionSettings**|**rsWrongItemType**|  
|**CreateReport**、 **CreateResource**、 **DeleteReportHistorySnapshot**、 **DeleteSchedule**、 **DeleteSubscription**、 **GetDataDrivenSubscriptionProperties**、 **GetSubscriptionProperties**、 **ListChildren**、 **ListScheduledReports**、 **PauseSchedule**、**レンダリング**、 **RenderStream**、 **ResumeSchedule**、 **SetCacheOptions**、 **SetDataDrivenSubscriptionProperties**、 **SetReportHistoryLimit**、 **SetReportHistoryOptions**、 **SetScheduleProperties**、 **SetSubscriptionProperties**|**rsParameterTypeMismatch**|  
|**CreateDataDrivenSubscription**、 **CreateDataSource**、 **CreateSchedule**、 **CreateSubscription**、 **FindItems**、 **GetReportParameters**、 **PrepareQuery**、**レンダリング**、 **SetCacheOptions**、 **SetDataDrivenSubscriptionProperties**、 **SetDataSourceContents**、 **SetPolicies**、 **SetReportDataSources**、 **SetReportParameters**、 **SetScheduleProperties**、 **SetSubscriptionProperties**、 **SetSystemPolicies**|**rsMissingElement**|  
|**CreateDataDrivenSubscription**、 **CreateDataSource**、 **CreateSchedule**、 **CreateSubscription**、 **PrepareQuery**、**レンダリング**、 **SetCacheOptions**、 **SetDataDrivenSubscriptionProperties**、 **SetDataSourceContents**、 **SetProperties**、 **SetReportDataSources**、 **SetReportParameters**、 **SetScheduleProperties**、 **SetSubscriptionProperties**、 **SetSystemProperties**|**rsInvalidElement**|  
|**CreateDataDrivenSubscription**、 **CreateSchedule**、 **CreateSubscription**、 **FindItems**、 **GetRenderResource**、 **PrepareQuery**、**レンダリング**、 **RenderStream**、 **SetCacheOptions**、 **SetDataDrivenSubscriptionProperties**、 **SetExecutionOptions**、 **SetProperties**、 **SetReportHistoryOptions**、 **SetReportParameters**、 **SetScheduleProperties**、 **SetSubscriptionProperties**、 **SetSystemProperties**|**rsElementTypeMismatch**|  
|**CreateDataSource**、 **CreateRole**、 **GetDataDrivenSubscriptionProperties**、 **GetRenderResource**、 **ListExtensions**、**レンダリング**、 **SetDataDrivenSubscriptionProperties**、 **SetDataSourceContents**、 **SetExecutionOptions**、 **SetReportHistoryLimit**、 **SetReportHistoryOptions**、 **SetScheduleProperties**|**rsInvalidParameter**|  
|**CreateDataDrivenSubscription**、 **CreateReportHistorySnapshot**、 **CreateSubscription**、 **PrepareQuery**、 **SetDataDrivenSubscriptionProperties**、 **SetExecutionOptions**、 **SetReportHistoryOptions**、 **SetSubscriptionProperties**|**rsInvalidDataSourceCredentialSetting**|  
|**CreateDataDrivenSubscriptionProperties**、 **CreateReportHistorySnapshot**、 **CreateSchedule**、 **CreateSubscription**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**、 **UpdateReportExecutionSnapshot**|**rsReportParameterValueNotSet**|  
|**CreateDataDrivenSubscription**、 **CreateSubscription**、 **GetExtensionSettings**、 **GetRenderResource**、**レンダリング**、 **RenderStream**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsMultipleExtensionsFoundInAssembly**|  
|**CreateDataDrivenSubscriptionProperties**、 **CreateSubscription**、**レンダリング**、 **SetCacheOptions**、 **SetExecutionOptions**、 **SetReportParameters**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsReportParameterTypeMismatch**|  
|**CreateSchedule**、 **CreateSubscription**、 **DeleteSchedule**、 **PauseSchedule**、 **ResumeSchedule**、 **SetCacheOptions**、 **SetExecutionOptions**、 **SetScheduleProperties**、 **SetSubscriptionProperties**|**rsSchedulerNotResponding**|  
|**DeleteSchedule**、 **GetScheduleProperties**、 **ListScheduledReports**、 **PauseSchedule**、 **ResumeSchedule**、 **SetCacheOptions**、 **SetExecutionOptions**、 **SetScheduleProperties**|**rsScheduleNotFound**|  
|**CreateDataDrivenSubscriptionProperties**、 **CreateSubscription**、**レンダリング**、 **SetReportParameters**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsReadOnlyReportParameter**|  
|**CreateDataDrivenSubscriptionProperties**、 **CreateSubscription**、 **GetReportParameters**、**レンダリング**、 **SetReportParameters**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsUnknownReportParameter**|  
|**DeleteSubscription**、 **GetDataDrivenSubscriptionProperties**、 **GetSubscriptionProperties**、 **SetDataDrivenSubscriptionProperties**、 **SetExecutionOptions**、 **SetSubscriptionProperties**|**rsSubscriptionNotFound**|  
|**CreateDataDrivenSubscription**、 **CreateSubscription**、 **GetExtensionSettings**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsDeliveryExtensionNotFound**|  
|**CreateDataDrivenSubscription**、 **CreateSubscription**、 **GetExtensionSettings**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsDeliveryError**|  
|**CreateDataDrivenSubscription**、 **GetDataDrivenSubscriptionProperties**、 **PrepareQuery**、 **SetDataDrivenSubscriptionProperties**|**rsSecureConnectionRequired**|  
|**CreateDataDrivenSubscription**、 **CreateSubscription**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsCannotSubscribeToEvent**|  
|**CreateDataDrivenSubscription**、 **CreateSubscription**、 **FireEvent**、 **SetDataDrivenSubscriptionProperties**、 **SetSubscriptionProperties**|**rsUnknownEventType**|  
|**CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateResource**、 **MoveItem**|**rsItemPathLengthExceeded**|  
|**CopyItem**、 **CreateFolder**、 **CreateReport**、 **CreateResource**、 **DeleteItem**|**rsReservedItem**|  
|**CreateDataSource**、 **SetDataSourceContents**、 **SetReportDataSources**|**rsInvalidElementCombination**|  
|**SetCacheOptions**、 **SetExecutionOptions**、 **SetReportHistoryOptions**|**rsInvalidParameterCombination**|  
|**CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateResource**、 **MoveItem**|**rsInvalidItemName**|  
|**CreateDataSource**、 **CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateResource**、 **MoveItem**|**rsItemAlreadyExists**|  
|**CreateFolder**、 **CreateLinkedReport**、 **CreateReport**、 **CreateResource**、 **SetProperties**|**rsReadOnlyProperty**|  
|**GetPolicies**、 **GetSystemPolicies**、 **SetPolicies**、 **SetSystemPolicies**|**rsInvalidPolicyDefinition**|  
|**SetCacheOptions**、 **SetDataSourceContents**、 **SetReportDataSources**、 **SetReportParameters**|**rsOperationPreventsUnattendedExecution**|  
|**CreateReportHistorySnapshot**、**レンダリング**、 **PrepareQuery**、 **UpdateReportExecutionSnapshot**|**rsInvalidDataSourceReference**|  
|**CreateReportHistorySnapshot**、 **PrepareQuery**、**レンダリング**、 **UpdateReportExecutionSnapshot**|**rsDataSourceDisabled**|  
|**CreateReport**、 **PrepareQuery**、 **SetReportDefinition**|**rsProcessingError**|  
|**GetRenderResource**、**レンダリング**、 **RenderStream**|**rsInvalidReportLink**|  
|**DeleteReportHistorySnapshot**、**レンダリング**、 **RenderStream**|**rsReportHistoryNotFound**|  
|**SetCacheOptions**、 **SetExecutionOptions**、 **SetReportHistoryOptions**|**rsReportMayNotBeScheduled**|  
|**CreateDataDrivenSubscription**、 **GetDataDrivenSubscriptionProperties**、 **SetDataDrivenSubscriptionProperties**|**rsOperationNotSupported**|  
|**CreateDataSource**、 **SetDataSourceContents**、 **SetReportDataSources**|**rsDataExtensionNotFound**|  
|**DeleteRole**、 **SetPolicies**、 **SetRoleProperties**|**rsRoleNotFound**|  
|**DeleteReportHistorySnapshot**、**レンダリング**、 **RenderStream**|**rsParametersNotSpecified**|  
|**GetReportParameters**、 **SetReportParameters**|**rsNotSupported**|  
|**SetReportParameters**、 **UpdateReportExecutionSnapshot**|**rsReportSnapshotNotEnabled**|  
|**CreateSchedule**、 **SetScheduleProperties**|**rsScheduleAlreadyExists**|  
|**CreateRole**、 **SetRoleProperties**|**rsTaskNotFound**|  
|**CreateRole**、 **SetRoleProperties**|**rsMixedTasks**|  
|**ListSubscriptions**、 **SetPolicies**|**rsUnknownUserName**|  
|**MoveItem**|**rsInvalidMove**|  
|**RenderStream**|**rsStreamNotFound**|  
|**RenderStream**|**rsMissingSessionId**|  
|**Render**|**rsReportNotReady**|  
|**Render**|**rsAssemblyNotPermissioned**|  
|**SetExecutionOptions**|**rsReportSnapshotEnabled**|  
|**FindItems**|**rsInvalidSearchOperator**|  
|**SetReportDataSources**|**rsDataSourceNotFound**|  
|**PrepareQuery**、**レンダリング**|**rsDataSourceNoPrompt**|  
|**PrepareQuery**|**rsCannotPrepareQuery**|  
|**DeleteRole**|**rsReservedRole**|  
|**CreateRole**|**rsEmptyRole**|  
|**InheritParentSecurity**|**rsInheritedPolicy**|  
|**CreateRole**|**rsRoleAlreadyExists**|  
|**InheritParentSecurity**|**rsCannotDeleteRootPolicy**|  
|**CancelJob**|**rsJobWasCanceled**|  
|**すべてのメソッド**|**rsServerConfigurationError**|  
  
## <a name="see-also"></a>参照  
 [Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [エラーとイベントのリファレンス & #40 です。Reporting Services &#41;](../../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Detail プロパティを使用して、特定のエラーを処理するには](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
