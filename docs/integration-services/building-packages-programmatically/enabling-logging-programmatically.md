---
title: "プログラムによるログ記録の有効化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- Integration Services packages, logs
- SSIS logging
- log providers [Integration Services]
- logs [Integration Services], enabling
- LoggingMode property
- LogProvider object
- packages [Integration Services], logs
ms.assetid: 3222a1ed-83eb-421c-b299-a53b67bba740
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: dd512f022832b57aa3fdcb85260926dd8354298c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="enabling-logging-programmatically"></a>プログラムによるログ記録の有効化
  ランタイム エンジンでは、パッケージの検証中および実行中にイベント固有の情報のキャプチャを有効にするための <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> オブジェクトのコレクションが提供されます。 <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> オブジェクトは、<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> オブジェクト群、つまり <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>、<xref:Microsoft.SqlServer.Dts.Runtime.Package>、<xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> などの各オブジェクトで使用できます。 ログ記録は、個別のコンテナーでも、パッケージ全体でも有効にすることができます。  
  
 コンテナーで使用できるログ プロバイダーには、いくつかの種類があります。 そのため、さまざまな形式でログ情報を作成し、保存することができます。 コンテナー オブジェクトをログ記録に登録するには、まずログ記録を有効にし、次にログ プロバイダーを選択するという、2 段階の処理が必要です。 コンテナーの <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> プロパティおよび <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> プロパティを使用して、ログ記録するイベントを指定し、ログ プロバイダーを選択します。  
  
## <a name="enabling-logging"></a>ログ記録の有効化  
 ログ記録を実行できる各コンテナーにある <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> プロパティは、コンテナーのイベント情報をイベント ログに記録するかどうかを指定します。 このプロパティには <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> 構造の値が割り当てられ、既定でコンテナーの親オブジェクトから継承されます。 コンテナーがパッケージで、そのため、親がない場合、プロパティを使用して、 <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>、既定値**無効になっている**です。  
  
### <a name="selecting-a-log-provider"></a>ログ プロバイダーの選択  
 後に、<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A>プロパティに設定されている**有効**に、ログ プロバイダーを追加、<xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders>プロセスを完了するコンテナーのコレクション。 <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> オブジェクトでは <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> コレクションが使用可能で、これにはコンテナーで選択されたログ プロバイダーが含まれています。 プロバイダーを作成し、コレクションに追加するには、<xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> メソッドを呼び出します。 このメソッドは、コレクションに追加されたログ プロバイダーを返します。 それぞれのプロバイダーには、そのプロバイダーに特有の構成設定があります。これらのプロパティは、<xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> プロパティを使用して設定します。  
  
 次の表に、使用可能なログ プロバイダー、説明、および <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 情報を示します。  
  
|プロバイダー|Description|ConfigString プロパティ|  
|--------------|-----------------|---------------------------|  
|SQL Server Profiler|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler でキャプチャおよび表示される SQL トレースを生成します。 このプロバイダーで使用されるファイル名の既定の拡張子は、.trc です。|構成は必要ありません。|  
|SQL Server|イベント ログ エントリを書き込みます、 **sysssislog**テーブルに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダーの場合は、データベースへの接続と対象データベースの名前を指定する必要があります。|  
|テキスト ファイル|イベント ログ エントリをコンマ区切り (CSV) 形式で ASCII テキスト ファイルに書き込みます。 このプロバイダーで使用されるファイル名の既定の拡張子は、.log です。|ファイル接続マネージャーの名前。|  
|Windows イベント ログ|ローカル コンピューター上のアプリケーション ログの標準 Windows イベント ログにログを記録します。|構成は必要ありません。|  
|XML ファイル|イベント ログ エントリを XML 形式ファイルに書き込みます。 このプロバイダーの既定のファイル名拡張子は .xml です。|ファイル接続マネージャーの名前。|  
  
 イベントに含めるかを設定して、イベント ログから除外、 **EventFilterKind**と**EventFilter**コンテナーのプロパティです。 **EventFilterKind**構造体には、2 つの値が含まれています。 **ExclusionFilter**と**InclusionFilter**、がかどうか、イベントを示すに追加、 **EventFilter**がイベント ログに記録します。 **EventFilter**プロパティは、フィルター選択の対象となるイベントの名前を格納する文字列配列を代入しています。  
  
 次のコードは、パッケージのログ記録を有効にし、<xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> コレクションにテキスト ファイルのログ プロバイダーを追加し、ログ出力に含めるイベントの一覧を指定します。  
  
## <a name="sample"></a>サンプル  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      ConnectionManager loggingConnection = p.Connections.Add("FILE");  
      loggingConnection.ConnectionString = @"C:\SSISPackageLog.txt";  
  
      LogProvider provider = p.LogProviders.Add("DTS.LogProviderTextFile.2");  
      provider.ConfigString = loggingConnection.Name;  
      p.LoggingOptions.SelectedLogProviders.Add(provider);  
      p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion;  
      p.LoggingOptions.EventFilter = new String[] { "OnPreExecute",   
         "OnPostExecute", "OnError", "OnWarning", "OnInformation" };  
      p.LoggingMode = DTSLoggingMode.Enabled;  
  
      // Add tasks and other objects to the package.  
  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
  
    Dim loggingConnection As ConnectionManager = p.Connections.Add("FILE")  
    loggingConnection.ConnectionString = "C:\SSISPackageLog.txt"  
  
    Dim provider As LogProvider = p.LogProviders.Add("DTS.LogProviderTextFile.2")  
    provider.ConfigString = loggingConnection.Name  
    p.LoggingOptions.SelectedLogProviders.Add(provider)  
    p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion  
    p.LoggingOptions.EventFilter = New String() {"OnPreExecute", _  
       "OnPostExecute", "OnError", "OnWarning", "OnInformation"}  
    p.LoggingMode = DTSLoggingMode.Enabled  
  
    ' Add tasks and other objects to the package.  
  
  End Sub  
  
End Module  
```  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;ログ記録](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  
