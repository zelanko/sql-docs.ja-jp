---
title: テーブル値パラメーター行セットの作成 |Microsoft ドキュメント
description: 静的および動的なテーブル値パラメーター行セットの作成
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8879c56eae2f5691a27a6261cc12ca3ad9c4cebc
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690255"
---
# <a name="table-valued-parameter-rowset-creation"></a>テーブル値パラメーターの行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  コンシューマーはテーブル値パラメーターに任意の行セット オブジェクトを使用できますが、通常の行セット オブジェクトはバックエンドのデータ ストアに対して実装されるため、パフォーマンスが制限されます。 このため、OLE DB Driver for SQL Server によりコンシューマーをメモリ内のデータの上に特殊化された行セット オブジェクトを作成できます。 この特殊なメモリ内の行セット オブジェクトは、テーブル値パラメーターの行セットと呼ばれる新しい COM オブジェクトです。 このオブジェクトには、パラメーター セットと同様の機能が用意されています。  
  
 テーブル値パラメーターの行セット オブジェクトは、コンシューマーが、複数のセッション レベルのインターフェイスを使用して、入力パラメーターに対して明示的に作成します。 テーブル値パラメーターごとのテーブル値パラメーター行セット オブジェクトの 1 つのインスタンスがあります。 コンシューマーは、既知のメタデータ情報を指定するか (静的なシナリオ)、プロバイダー インターフェイスを使用してメタデータ情報を検出する (動的なシナリオ) ことにより、テーブル値パラメーターの行セット オブジェクトを作成できます。 この後の各セクションで、これらの 2 つのシナリオについて説明します。  
  
## <a name="static-scenario"></a>静的なシナリオ  
 型情報がわかっている場合、コンシューマーは、テーブル値パラメーターに対応するテーブル値パラメーター行セット オブジェクトをインスタンス化 ITableDefinitionWithConstraints::CreateTableWithConstraints を使用します。  
  
 *Guid*フィールド (*pTableID*パラメーター) 特別な GUID (CLSID_ROWSET_TVP) が含まれています。 *PwszName*メンバーには、コンシューマーがインスタンス化するテーブル値パラメーターの型の名前が含まれています。 *EKind* DBKIND_GUID_NAME にフィールドが設定されます。 ステートメントがアドホック SQL 以外の場合は、この名前が必要名前は、プロシージャ呼び出しである場合は省略可能です。  
  
 集計、コンシューマーが渡されます、 *pUnkOuter* controlling IUnknown のパラメーターです。  
  
 テーブル値パラメーター行セット オブジェクトのプロパティは読み取り専用に、コンシューマーは、プロパティで設定を想定されていません*rgPropertySets*です。  
  
 *RgPropertySets*各 DBCOLUMNDESC 構造体、コンシューマーのメンバーは、各列の追加のプロパティを指定できます。 これらのプロパティは、DBPROPSET_SQLSERVERCOLUMN プロパティ セットに属しています。 これらのプロパティによって、列ごとに計算の設定と既定の設定を指定できます。 また、NULL 値の許容や ID など、列の既存のプロパティもサポートされます。  
  
 テーブル値パラメーター行セット オブジェクトから対応する情報を取得するには、は、コンシューマーは、irowsetinfo: を使用します。  
  
 各列の状態を計算するには、null、一意、に関する情報を取得および更新、コンシューマーは、icolumnsrowset::getcolumnsrowset または icolumnsinfo::getcolumninfo を使用できます。 これらのメソッドでは、各テーブル値パラメーターの行セットの列に関する詳細情報が取得できます。  
  
 コンシューマーは、テーブル値パラメーターの列ごとに型を指定します。 内のテーブルが作成されるときに列を指定する方法に似ています[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 コンシューマーは、を介して SQL Server の OLE DB ドライバーからテーブル値パラメーター行セット オブジェクトを取得、 *ppRowset*出力パラメーターです。  
  
## <a name="dynamic-scenario"></a>動的なシナリオ  
 コンシューマーで型情報がない場合は、テーブル値パラメーター行セット オブジェクトをインスタンス化 iopenrowset::openrowset を使用してください。 すべてのコンシューマーは、プロバイダーに型名を知らせる必要があります。  
  
 このシナリオでは、プロバイダーがコンシューマーに代わって、テーブル値パラメーターの行セット オブジェクトに関する型情報をサーバーから取得します。  
  
 *PTableID*と*pUnkOuter*パラメーターは、静的なシナリオのように設定する必要があります。 SQL Server の OLE DB Driver 型情報 (列情報と制約)、サーバーから取得し、を通じて、テーブル値パラメーター行セット オブジェクトを返す、 *ppRowset*パラメーター。 この操作は、サーバーとの通信が必要です、したがってだけでなく、静的なシナリオを実行しません。 動的なシナリオは、パラメーター化されたプロシージャ呼び出しでのみ動作します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターを使用して&#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
