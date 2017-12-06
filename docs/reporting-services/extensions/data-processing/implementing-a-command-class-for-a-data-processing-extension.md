---
title: "データ処理拡張機能の Command クラスの実装 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
caps.latest.revision: "35"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 582f94ca125b8d8e00960e68640e2ae616340f2f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>データ処理拡張機能の Command クラスの実装
  **Command** オブジェクトを使用して、要求を作成し、それをデータ ソースに渡します。 コマンド テキストは、テキスト、XML など多くのさまざまな構文形式を使用できます。 結果が返されると、**Command** オブジェクトは、**DataReader** オブジェクトとして結果を返します。  
  
 **Command** クラスを作成するには、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> を実装します。 **DataReader** オブジェクトとして結果セットを返すには、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> メソッドを実装します。 **Command** クラスの <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> メソッドには、引数として <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> 列挙を取得する実装を含める必要があります。 データ処理拡張機能をレポート デザイナーに配置するには、<xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> メソッドで <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> の場合を処理する実装を含める必要があります。 スキーマだけの実装は、レポート デザイナーにフィールド一覧を提供するために使用します。 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> メソッドによって返される **DataReader** オブジェクトは、フィールド、つまり、列の型および名前の情報を結果セットに含める必要があります。  
  
 必要に応じて、**Command** クラスは <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装できます。 このインターフェイスにより、実装クラスでクエリを分析して、クエリのパラメーターの一覧を返すことができます。 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> インターフェイスの機能を使用できるのはレポート デザイナーだけです。 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装すると、レポート デザイナーのユーザーがプレビュー モードでレポートを実行するたびに、ユーザーにパラメーターを入力するように要求できます。 さらに、**[データセット]** ダイアログの **[パラメーター]** タブでパラメーターを表示できます。  
  
> [!NOTE]  
>  カスタム データ処理拡張機能でパラメーターをサポートしない場合は、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装する必要はありません。  
  
 **Command** クラス実装の例については、「[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
