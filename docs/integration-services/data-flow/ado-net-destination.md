---
title: "ADO NET 変換先 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.adonetdest.f1"
helpviewer_keywords: 
  - "変換先 [Integration Services], ADO.NET"
  - "ADO.NET 変換先"
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ADO NET 変換先
  ADO NET 変換先では、データベースのテーブルやビューを使用する、さまざまな [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 互換データベースにデータを読み込みます。 このデータを既存のテーブルやビューに読み込むことができますが、新しいテーブルを作成して、そこにデータを読み込むこともできます。  
  
 ADO NET 変換先を使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]に接続できます。 OLE DB を使用した [!INCLUDE[ssSDS](../../includes/sssds-md.md)] への接続はサポートされていません。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の詳細については、「[一般的なガイドラインと制限事項 (Windows Azure SQL データベース)](http://go.microsoft.com/fwlink/?LinkId=248228)」を参照してください。  
  
## ADO NET 変換先のトラブルシューティング  
 ADO NET 変換先による外部データ プロバイダーの呼び出しをログに記録できます。 このログ機能を使用すると、ADO NET 変換先による外部データ ソースへのデータ保存に関するトラブルシューティングを行えます。 ADO NET 変換先による外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。 詳細については、「[パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。  
  
## ADO NET 変換先の構成  
 この変換先は [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用してデータ ソースに接続します。また、この接続マネージャーでは、使用する [!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーを指定します。 詳細については、「[ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md)」(ADO.NET 接続マネージャー) を参照してください。  
  
 ADO NET 変換先には、入力列と変換先データ ソースの列との間のマッピングが含まれています。 入力列を変換先のすべての列にマップする必要はありません。 ただし、一部の変換先列のプロパティで、入力列のマップが必要になることがあります。 マップしない場合、エラーが発生することがあります。 たとえば、変換先列で NULL 値が許容されていない場合は、入力列をその変換先列にマップする必要があります。 また、マップされる列のデータ型には互換性がある必要があります。 たとえば、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーで文字列データ型の入力列を数値データ型の変換先列にマップすることがサポートされていなければ、その操作はできません。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、データ型が IMAGE 型に設定された列にテキストを挿入することはサポートされていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型の詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
>  ADO NET 変換先では、DT_DBTIME 型に設定されている入力列を datetime 型に設定されているデータベース列にマップすることがサポートされていません。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のデータ型について詳しくは、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」をご覧ください。  
  
 ADO NET 変換先は、1 つの標準入力と 1 つのエラー出力をとります。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[ADO NET 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[ADO NET 変換先エディター] ([接続マネージャー] ページ)](../Topic/ADO%20NET%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)  
  
-   [[ADO NET 変換先エディター] &#40;[マッピング] ページ&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Mappings%20Page\).md)  
  
-   [[ADO NET 変換先エディター] &#40;[エラー出力] ページ&#41;](../Topic/ADO%20NET%20Destination%20Editor%20\(Error%20Output%20Page\).md)  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [ADO NET カスタム プロパティ](../../integration-services/data-flow/ado-net-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  