---
title: ADO.NET 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 850c8f0f54339594b19debd48ebf4ac7021873d3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921247"
---
# <a name="adonet-connection-manager"></a>ADO.NET 接続マネージャー
  [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用すると、パッケージは .NET プロバイダーを使用してデータ ソースにアクセスできます。 この接続マネージャーは通常、などのデータソースにアクセスするために使用され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。また、C# などの言語を使用してマネージコードで記述されたカスタムタスクで、OLE DB と XML を介して公開されるデータソースにもアクセスします。  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)]接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時に接続として解決される接続マネージャーを作成し、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーのプロパティを設定して、接続マネージャーをパッケージのコレクションに追加し `Connections` ます。  
  
 接続マネージャーの `ConnectionManagerType` プロパティは、`ADO.NET` に設定されます。 `ConnectionManagerType` の値には、接続マネージャーが使用する .NET プロバイダーの名前を含めることができます。  
  
## <a name="adonet-connection-manager-troubleshooting"></a>ADO.NET 接続マネージャーのトラブルシューティング  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択する必要があります。 詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーに読み込まれると、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日付データ型のデータは次の表に示す結果を生成します。  
  
|SQL Server のデータ型|結果|  
|--------------------------|------------|  
|`time`, `datetimeoffset`|パッケージがパラメーター化 SQL コマンドを使用していない場合、パッケージは失敗します。 パラメーター化 SQL コマンドを使用するには、パッケージで SQL 実行タスクを使用します。 詳細については、「 [SQL 実行タスク](../control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。|  
|`datetime2`|[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーは、ミリ秒の値を切り捨てます。|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の詳細とそれを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型にマッピングする方法については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」と「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="adonet-connection-manager-configuration"></a>ADO.NET 接続マネージャーの構成  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーは、次の方法で構成できます。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
-   選択した .NET プロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。  
  
-   プロパイダによっては、接続先のデータ ソースの名前を指定します。  
  
-   選択したプロバイダーに適したセキュリティ資格情報を指定します。  
  
-   接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。  
  
 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーの多くの構成オプションは、接続マネージャーが使用する .NET プロバイダーによって異なります。  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[ADO.NET の接続マネージャーの構成]](../configure-ado-net-connection-manager.md)  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; の接続](integration-services-ssis-connections.md)  
  
  
