---
title: "データ処理拡張機能のコマンド クラスの実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: b601aa43ecce5347f7229999455360be761f3bd3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>データ処理拡張機能の Command クラスの実装
  **コマンド**オブジェクトが要求を作成し、データ ソースに渡します。 コマンド テキストは、テキスト、XML など多くのさまざまな構文形式を使用できます。 結果が返される場合は、**コマンド**オブジェクトとして結果が返されます、 **DataReader**オブジェクト。  
  
 作成する、**コマンド**クラスを実装<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>です。 実装、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>としての結果を返す方法を設定、 **DataReader**オブジェクト。 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>のメソッド、**コマンド**クラスは、取得する実装を含める必要があります、<xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior>列挙体を引数として。 データ処理拡張機能をレポート デザイナーに配置するには、<xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> メソッドで <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> の場合を処理する実装を含める必要があります。 スキーマだけの実装は、レポート デザイナーにフィールド一覧を提供するために使用します。 **DataReader**によって返されるオブジェクト、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>メソッドは、フィールドの型と名前の情報を格納する必要がありますまたは列の場合、結果セットです。  
  
 必要に応じて、**コマンド**クラスで実装できる<xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>です。 このインターフェイスにより、実装クラスでクエリを分析して、クエリのパラメーターの一覧を返すことができます。 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> インターフェイスの機能を使用できるのはレポート デザイナーだけです。 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装すると、レポート デザイナーのユーザーがプレビュー モードでレポートを実行するたびに、ユーザーにパラメーターを入力するように要求できます。 さらでパラメーターを表示することができます、**パラメーター**のタブ、**データ セット**ダイアログ。  
  
> [!NOTE]  
>  カスタム データ処理拡張機能でパラメーターをサポートしない場合は、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装する必要はありません。  
  
 サンプルの**コマンド**クラス実装を参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
