---
title: SqlErrorLogEvent Class |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 95588b82a36bb5d7d5d520a5f54ca968a9198112
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076149"
---
# <a name="sqlerrorlogevent-class"></a>SqlErrorLogEvent クラス
  指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイル内のイベントの表示に関するプロパティを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a>[プロパティ]  
 SQLErrorLogEvent クラスでは、次のプロパティを定義します。  
  
|||  
|-|-|  
|FileName|データ型: `string`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> エラー ログ ファイルの名前です。|  
|InstanceName|データ型: `string`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> 修飾子: キー<br /><br /> ログ ファイルが存在する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|よう|データ型: `datetime`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> 修飾子: キー<br /><br /> <br /><br /> イベントがログ ファイルに記録された日時。|  
|メッセージ|データ型: `string`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> イベント メッセージ。|  
|ProcessInfo|データ型: `string`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> イベントのソース サーバー プロセス ID (SPID) に関する情報。|  
  
## <a name="remarks"></a>コメント  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>例  
 次の例では、指定したログ ファイルに記録されたすべてのイベントの値を取得する方法を示します。 実行するには例では、置換\< *Instance_Name*> のインスタンスの名前を持つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、置換 'errorlog.1' など、エラー ログ ファイルの名前を持つ ' File_Name'、'Instance1' などです。  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a>コメント  
 ときに*InstanceName*または*FileName*が指定されていないステートメントでは、WQL クエリは、既定のインスタンスと現在の情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルです。 たとえば、次の WQL ステートメントは、現在のログ ファイル (ERRORLOG) の既定のインスタンス (MSSQLSERVER) からすべてのログ イベントを返します。  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Security  
 接続する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルは、WMI からは、ローカルおよびリモートの両方のコンピューターで次のアクセス許可が必要があります。  
  
-   読み取りアクセス、 **root \microsoft\sqlserver\computermanagement10** WMI 名前空間。 既定では、すべてのユーザーがアカウントの有効化権限による読み取りアクセスを持ちます。  
  
-   エラー ログを格納したフォルダーへの読み取り権限。 既定では、エラー ログは、次のパスにあります (ここで\<*ドライブ >* インストール先ドライブを表す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と\< *InstanceName*> は、インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。  
  
     **\<ドライブ >: \Program Files\Microsoft SQL Server\MSSQL12** **.\<InstanceName > \MSSQL\Log**  
  
 ファイアウォール経由で接続する場合は、接続先のリモート コンピューターのファイアウォールで WMI 用に例外が設定されていることを確認する必要があります。 詳細については、次を参照してください。 [WMI は、Windows Vista でリモート起動に接続する](http://go.microsoft.com/fwlink/?LinkId=178848)です。  
  
## <a name="see-also"></a>参照  
 [SqlErrorLogFile クラス](sqlerrorlogfile-class.md)   
 [オフライン ログ ファイルの表示](../logs/view-offline-log-files.md)  
  
  