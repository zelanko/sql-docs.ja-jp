---
title: "プログラムによる接続マネージャーの操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9093b9eadce231aea248cd04c2b57dc5dd5e1a76
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-connection-managers-programmatically"></a>プログラムによる接続マネージャーの操作
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]、関連付けられている接続マネージャー クラスの AcquireConnection メソッドがマネージ コード内の接続マネージャーを使用している場合は最も頻繁に呼び出すメソッド。 マネージ コードを記述するときに、manager 接続の機能を使用して、AcquireConnection メソッドを呼び出す必要があります。 このメソッドは、マネージ コードを記述する場所がスクリプト タスク、スクリプト コンポーネント、カスタム オブジェクト、またはカスタム アプリケーションのいずれであっても、呼び出す必要があります。  
  
 AcquireConnection メソッドを正常に呼び出すには、次の質問に対する回答を認識する必要が。  
  
-   **AcquireConnection メソッドからマネージ オブジェクトを返す接続マネージャー**  
  
     多くの接続マネージャーは、マネージ コードからアンマネージ COM オブジェクト (System.__ComObject) およびこれらのオブジェクトを使用することはできません簡単に返します。 このような接続マネージャーには、使用頻度の高い OLE DB 接続マネージャーも含まれます。  
  
-   **マネージ オブジェクトを返す接続マネージャーで、どのようなオブジェクトは AcquireConnection メソッドを返す**  
  
     戻り値を適切な型をキャストするには、AcquireConnection メソッドが返すオブジェクトの種類を知っている必要があります。 たとえば、AcquireConnection メソッドの[!INCLUDE[vstecado](../includes/vstecado-md.md)]SqlClient プロバイダーを使用すると、接続マネージャーが開いている SqlConnection オブジェクトを返します。 ただし、ファイル接続マネージャーの AcquireConnection メソッドには、文字列だけを返します。  
  
 このトピックでは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に付属の接続マネージャーについて、上記の点を説明します。  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>マネージ オブジェクトを返さない接続マネージャー  
 次の表は、AcquireConnection メソッドからネイティブ COM オブジェクト (System.__ComObject) を返す接続マネージャーを一覧表示します。 これらのアンマネージ オブジェクトは、マネージ コードから簡単には使用できません。  
  
|接続マネージャーの種類|接続マネージャー名|  
|-----------------------------|-----------------------------|  
|ADO (ADO)|ADO 接続マネージャー|  
|MSOLAP90|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接続マネージャー|  
|EXCEL|Excel 接続マネージャー|  
|FTP|FTP 接続マネージャー|  
|HTTP|HTTP 接続マネージャー|  
|ODBC|ODBC 接続マネージャー|  
|OLEDB|OLE DB 接続マネージャー|  
  
 通常、使用することができます、 [!INCLUDE[vstecado](../includes/vstecado-md.md)] ADO、Excel、ODBC、または OLE DB データ ソースに接続するマネージ コードからの接続マネージャーです。  
  
## <a name="return-values-from-the-acquireconnection-method"></a>AcquireConnection メソッドからの戻り値  
 次の表は、AcquireConnection メソッドからマネージ オブジェクトを返す接続マネージャーを一覧表示します。 これらのマネージ オブジェクトは、マネージ コードから簡単に使用できます。  
  
|接続マネージャーの種類|接続マネージャー名|戻り値の型|追加情報|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|[!INCLUDE[vstecado](../includes/vstecado-md.md)] 接続マネージャー|**System.Data.SqlClient.SqlConnection**||  
|FILE|ファイル接続マネージャー|**System.String**|ファイルへのパス。|  
|FLATFILE|フラット ファイル接続マネージャー|**System.String**|ファイルへのパス。|  
|MSMQ (MSMQ)|MSMQ 接続マネージャー|**System.Messaging.MessageQueue**||  
|MULTIFILE|複数ファイル接続マネージャー|**System.String**|いずれかのファイルへのパス。|  
|MULTIFLATFILE|複数フラット ファイル接続マネージャー|**System.String**|いずれかのファイルへのパス。|  
|SMOServer|SMO 接続マネージャー|**Microsoft.SqlServer.Management.Smo.Server**||  
|SMTP (SMTP)|SMTP 接続マネージャー|**System.String**|例: `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`|  
|WMI (WMI)|WMI 接続マネージャー|**System.Management.ManagementScope**||  
|SQLMOBILE|SQL Server Compact 接続マネージャー|**System.Data.SqlServerCe.SqlCeConnection**||  
  
## <a name="see-also"></a>参照  
 [スクリプト タスク内のデータ ソースに接続します。](../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [スクリプト コンポーネントでデータ ソースに接続します。](../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [カスタム タスクでのデータ ソースへの接続](../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  

