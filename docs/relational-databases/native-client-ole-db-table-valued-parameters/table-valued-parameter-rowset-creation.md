---
title: テーブル値パラメーター行セットの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
ms.assetid: ffe213ca-cc0e-465e-b31c-a8272324c4fe
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c7202570f46ac3ba8045ab825ddd1874f64dd6b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameter-rowset-creation"></a>テーブル値パラメーターの行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コンシューマーはテーブル値パラメーターに任意の行セット オブジェクトを使用できますが、通常の行セット オブジェクトはバックエンドのデータ ストアに対して実装されるため、パフォーマンスが制限されます。 このため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、コンシューマーがメモリ内データの上位に特殊な行セット オブジェクトを作成できます。 この特別なメモリ内の行セット オブジェクトは、テーブル値パラメーター行セットと呼ばれる新しい COM オブジェクトです。 このオブジェクトには、パラメーター セットと同様の機能が用意されています。  
  
 テーブル値パラメーターの行セット オブジェクトは、コンシューマーが、複数のセッション レベルのインターフェイスを使用して、入力パラメーターに対して明示的に作成します。 テーブル値パラメーターの行セット オブジェクトは、テーブル値パラメーターごとに 1 つのインスタンスがあります。 コンシューマーは、既知のメタデータ情報を指定するか (静的なシナリオ)、プロバイダー インターフェイスを使用してメタデータ情報を検出する (動的なシナリオ) ことにより、テーブル値パラメーターの行セット オブジェクトを作成できます。 この後の各セクションで、これらの 2 つのシナリオについて説明します。  
  
## <a name="static-scenario"></a>静的なシナリオ  
 型情報がわかっている場合、コンシューマーは、テーブル値パラメーターに対応するテーブル値パラメーター行セット オブジェクトをインスタンス化 ITableDefinitionWithConstraints::CreateTableWithConstraints を使用します。  
  
 *Guid*フィールド (*pTableID*パラメーター) 特別な GUID (CLSID_ROWSET_TVP) が含まれています。 *PwszName*メンバーには、コンシューマーがインスタンス化するテーブル値パラメーターの型の名前が含まれています。 *EKind* DBKIND_GUID_NAME にフィールドが設定されます。 この名前は、ステートメントがアドホック SQL の場合に必要です。プロシージャ呼び出しの場合、名前は省略可能です。  
  
 集計、コンシューマーが渡されます、 *pUnkOuter* controlling IUnknown のパラメーターです。  
  
 テーブル値パラメーター行セット オブジェクトのプロパティは読み取り専用プロパティを設定するすべてコンシューマーが予期されていません*rgPropertySets*です。  
  
 *RgPropertySets*各 DBCOLUMNDESC 構造体、コンシューマーのメンバーは、各列の追加のプロパティを指定できます。 これらのプロパティは、DBPROPSET_SQLSERVERCOLUMN プロパティ セットに属しています。 これらのプロパティによって、列ごとに計算の設定と既定の設定を指定できます。 また、NULL 値の許容や ID など、列の既存のプロパティもサポートされます。  
  
 テーブル値パラメーター行セット オブジェクトから対応する情報を取得するには、は、コンシューマーは、irowsetinfo: を使用します。  
  
 各列の状態を計算するには、null、一意、に関する情報を取得および更新は、コンシューマーは、icolumnsrowset::getcolumnsrowset または icolumnsinfo::getcolumninfo を使用します。 これらのメソッドでは、各テーブル値パラメーターの行セットの列に関する詳細情報が取得できます。  
  
 コンシューマーは、テーブル値パラメーターの列ごとに型を指定します。 この方法は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でテーブルを作成する際に列を指定する方法と似ています。 コンシューマーからテーブル値パラメーター行セット オブジェクトを取得する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを介して、 *ppRowset*出力パラメーターです。  
  
## <a name="dynamic-scenario"></a>動的なシナリオ  
 コンシューマーが型情報を持っていない場合に、テーブル値パラメーター行セット オブジェクトをインスタンス化 iopenrowset::openrowset を使用してください。 すべてのコンシューマーは、プロバイダーに型名を知らせる必要があります。  
  
 このシナリオでは、プロバイダーがコンシューマーに代わって、テーブル値パラメーターの行セット オブジェクトに関する型情報をサーバーから取得します。  
  
 *PTableID*と*pUnkOuter*パラメーターは、静的なシナリオのように設定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、サーバーから型情報 (列情報と制約) を取得し、オブジェクトを取得するテーブル値パラメーター行セットから、 *ppRowset*パラメーター。 この操作は、サーバーとの通信を必要とされ、したがってパフォーマンスが低く、静的なシナリオ。 動的なシナリオは、パラメーター化されたプロシージャ呼び出しでのみ動作します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
