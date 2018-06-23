---
title: SqlErrorLogFile Class |Microsoft ドキュメント
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
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5e23c4512f04370fa24b3eb4ff3b74a072f6a2e5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166045"
---
# <a name="sqlerrorlogfile-class"></a>SqlErrorLogFile クラス
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルの情報の表示に関するプロパティを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>[プロパティ]  
 SQLErrorLogFile クラスでは、次のプロパティを定義します。  
  
|||  
|-|-|  
|ArchiveNumber|データ型: `uint32`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> ログ ファイルのアーカイブ番号。|  
|InstanceName|データ型: `string`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> 修飾子: キー<br /><br /> <br /><br /> ログ ファイルが存在する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|LastModified|データ型: `datetime`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> ログ ファイルの最終変更日。|  
|LogFileSize|データ型: `uint32`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> <br /><br /> ログ ファイルのサイズ (バイト単位)。|  
|名前|データ型: `string`<br /><br /> アクセスの種類: 読み取り専用<br /><br /> 修飾子: キー<br /><br /> <br /><br /> ログ ファイルの名前。|  
  
## <a name="remarks"></a>コメント  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>例  
 次の例では、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にあるすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルに関する情報を取得します。 例を実行するには、置換\< *Instance_Name*> インスタンス 'Instance1' などの名前に置き換えます。  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>コメント  
 ときに*InstanceName*が指定されていないステートメントでは、WQL クエリは、既定のインスタンスの情報を返します。 たとえば、次の WQL ステートメントは、既定のインスタンス (MSSQLSERVER) からすべてのログ ファイルに関する情報を返します。  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Security  
 接続する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルは、WMI からは、ローカルおよびリモートの両方のコンピューターで次のアクセス許可が必要があります。  
  
-   読み取りアクセス、 **root \microsoft\sqlserver\computermanagement10** WMI 名前空間。 既定では、すべてのユーザーがアカウントの有効化権限による読み取りアクセスを持ちます。  
  
    > [!NOTE]  
    >  WMI 権限を確認する方法については、トピックの [セキュリティ] セクションを参照してください。[オフライン ログ ファイルの表示](../logs/view-offline-log-files.md)です。  
  
-   エラー ログを格納したフォルダーへの読み取り権限。 既定では、エラー ログは、次のパスにあります (ここで\<*ドライブ >* インストール先ドライブを表す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と\< *InstanceName*> は、インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。  
  
     **\<ドライブ >: \Program Files\Microsoft SQL Server\MSSQL11** **.\<InstanceName > \MSSQL\Log**  
  
 ファイアウォール経由で接続する場合は、接続先のリモート コンピューターのファイアウォールで WMI 用に例外が設定されていることを確認する必要があります。 詳細については、次を参照してください。 [WMI は、Windows Vista でリモート起動に接続する](http://go.microsoft.com/fwlink/?LinkId=178848)です。  
  
## <a name="see-also"></a>参照  
 [SqlErrorLogEvent クラス](sqlerrorlogevent-class.md)   
 [オフライン ログ ファイルの表示](../logs/view-offline-log-files.md)  
  
  