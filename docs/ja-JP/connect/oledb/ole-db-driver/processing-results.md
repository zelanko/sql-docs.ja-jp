---
title: 結果の処理 |Microsoft ドキュメント
description: 結果の処理
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3e157a115fcc0efd1935a1caa86da18d9afe7c71
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="processing-results"></a>結果の処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  コマンドの実行、またはプロバイダーからの行セット オブジェクトの直接生成のいずれかによって行セット オブジェクトを作成する場合、コンシューマーはその行セット内のデータにアクセスして、データを取得する必要があります。  
  
 行セットは、表形式でデータを公開する SQL Server の OLE DB ドライバーを有効にするサーバーの全体のオブジェクトです。 概念的には、行セットは行の集まりを表し、各行には列データが格納されています。 行セット オブジェクトなどのインターフェイスを公開**IRowset** (行セットから行を順番にフェッチするメソッドを含む)、 **IAccessor** (表形式のデータがコンシューマー プログラム変数にバインドする方法を説明する列のバインドのグループの定義を許可する) **IColumnsInfo** (行セットの列に関する情報を提供します)、および**IRowsetInfo** (行セットに関する情報を提供します)。  
  
 コンシューマーが呼び出すことができます、 **irowset::getdata**バッファーに行セットから 1 行のデータを取得します。 前に**GetData**が呼び出されると、コンシューマーは DBBINDING 構造体のセットを使用してバッファーについて説明します。 各バインドは、行セット内の列をコンシューマーのバッファーに格納する方法を記述するもので、次の情報が含まれます。  
  
-   バインドが適用される列 (パラメーター) の序数  
  
-   バインドされる内容 (データ値、データの長さ、バインドの状態など) に関する情報  
  
-   バッファー内の各部分へのオフセットに関する情報  
  
-   コンシューマーのバッファー内でのデータ値の長さと型  
  
 プロバイダーはデータを取得するときに、各バインドの情報を使用してコンシューマーのバッファーからデータを取得する位置と方法を決定します。 また、コンシューマーのバッファーにデータを設定するときに、各バインドの情報を使用してコンシューマーのバッファー内にあるデータを返す位置と方法を決定します。  
  
 DBBINDING 構造体を指定したら、アクセサーを作成 (**iaccessor::createaccessor**)。 バインドの集まりであるアクセサーは、コンシューマーのバッファー内のデータを取得または設定するときに使用します。  
  
## <a name="see-also"></a>参照  
 [SQL Server アプリケーション用の OLE DB ドライバーを作成します。](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [OLE DB の操作方法に関するトピック](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
