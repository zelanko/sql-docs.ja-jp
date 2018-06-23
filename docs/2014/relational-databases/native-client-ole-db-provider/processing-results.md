---
title: 結果の処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7b1f2d039cf88e8487433d0d92e2e0f6c265f637
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072309"
---
# <a name="processing-results"></a>結果の処理
  コマンドの実行、またはプロバイダーからの行セット オブジェクトの直接生成のいずれかによって行セット オブジェクトを作成する場合、コンシューマーはその行セット内のデータにアクセスして、データを取得する必要があります。  
  
 行セットは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが表形式でデータを公開できるようにするための重要な機能を持つオブジェクトです。 概念的には、行セットは行の集まりを表し、各行には列データが格納されています。 行セット オブジェクトなどのインターフェイスを公開**IRowset** (行セットから行を順番にフェッチするメソッドを含む)、 **IAccessor** (を記述する列のバインドのグループの定義を許可します方法表形式のデータがコンシューマー プログラム変数にバインド)、 **IColumnsInfo** (行セットの列に関する情報を提供します)、および**IRowsetInfo** (行セットに関する情報を提供します)。  
  
 コンシューマーが呼び出すことができます、 **irowset::getdata**バッファーに行セットから 1 行のデータを取得します。 前に**GetData**が呼び出されると、コンシューマーは DBBINDING 構造体のセットを使用してバッファーについて説明します。 各バインドは、行セット内の列をコンシューマーのバッファーに格納する方法を記述するもので、次の情報が含まれます。  
  
-   バインドが適用される列 (パラメーター) の序数  
  
-   バインドされる内容 (データ値、データの長さ、バインドの状態など) に関する情報  
  
-   バッファー内の各部分へのオフセットに関する情報  
  
-   コンシューマーのバッファー内でのデータ値の長さと型  
  
 プロバイダーはデータを取得するときに、各バインドの情報を使用してコンシューマーのバッファーからデータを取得する位置と方法を決定します。 また、コンシューマーのバッファーにデータを設定するときに、各バインドの情報を使用してコンシューマーのバッファー内にあるデータを返す位置と方法を決定します。  
  
 DBBINDING 構造体を指定したら、アクセサーを作成 (**iaccessor::createaccessor**)。 バインドの集まりであるアクセサーは、コンシューマーのバッファー内のデータを取得または設定するときに使用します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client OLE DB プロバイダー アプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [OLE DB の使用法に関するトピック](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  