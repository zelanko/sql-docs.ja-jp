---
title: "データ処理拡張機能の DataReader クラスの実装 |Microsoft ドキュメント"
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
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: fb0f4c2f3ea3137f2e614e688aa5e3823a043e50
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>データ処理拡張機能の DataReader クラスの実装
  **DataReader**オブジェクト データ ソースからデータの読み取り専用、前方参照専用のストリームを取得するクライアントを有効にします。 結果が返されるようにクエリを実行し、それらを要求するまで、クライアントのネットワーク バッファーに格納されますを使用して、**読み取り**のメソッド、 **DataReader**クラスです。 作成する、 **DataReader**クラスを実装<xref:Microsoft.ReportingServices.DataProcessing.IDataReader>し、必要に応じて実装<xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>です。 使用して、 **DataReader**オブジェクト増加アプリケーションのパフォーマンスとすぐにデータを取得することによってはシステム オーバーヘッドの削減、メモリ内の時に、返されると (既定) のファイルを格納する 1 つの行にクエリの結果全体の待機中ではなく、使用可能な。  
  
 インスタンスを作成した後、**コマンド**クラスを作成する、 **DataReader**呼び出して**Command.ExecuteReader**データ ソースから行を取得します。 **DataReader**実装は、次の 2 つの基本的な機能を提供する必要があります。 前方参照専用のアクセスの実行結果にコマンドと列の型、名前、へのアクセスを実行することによって取得された設定と各行内の値。 クライアントを使用して、**読み取り**のメソッド、 **DataReader**クエリの結果から行を取得するオブジェクト。  
  
 レポート デザイナーで、 **DataReader**フィールドだけでなく、結果セットに関するスキーマ情報の一覧を取得するオブジェクトを使用します。 これを実装することによって実現、 **GetName**、 **GetValue**、 **GetFieldType**と**GetOrdinal**のメソッド、<xref:Microsoft.ReportingServices.DataProcessing.IDataReader>インターフェイスです。  
  
 <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> インターフェイスでは、結果セットに関する特定の集計情報を指定できます。 サンプルの**DataReader**クラス実装を参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
