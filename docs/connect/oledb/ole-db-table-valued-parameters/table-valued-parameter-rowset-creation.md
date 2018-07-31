---
title: テーブル値パラメーター行セットの作成 |Microsoft Docs
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
ms.openlocfilehash: 9a809f4469f46a94053612a64119d88f581930fb
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108034"
---
# <a name="table-valued-parameter-rowset-creation"></a>テーブル値パラメーターの行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  コンシューマーはテーブル値パラメーターに任意の行セット オブジェクトを使用できますが、通常の行セット オブジェクトはバックエンドのデータ ストアに対して実装されるため、パフォーマンスが制限されます。 このため、OLE DB Driver for SQL Server では、コンシューマーがメモリ内データの上位に特殊な行セット オブジェクトを作成できます。 この特殊なメモリ内の行セット オブジェクトは、テーブル値パラメーターの行セットと呼ばれる新しい COM オブジェクトです。 このオブジェクトには、パラメーター セットと同様の機能が用意されています。  
  
 テーブル値パラメーターの行セット オブジェクトは、コンシューマーが、複数のセッション レベルのインターフェイスを使用して、入力パラメーターに対して明示的に作成します。 テーブル値パラメーターの行セット オブジェクトは、テーブル値パラメーターごとに 1 つのインスタンスがあります。 コンシューマーは、既知のメタデータ情報を指定するか (静的なシナリオ)、プロバイダー インターフェイスを使用してメタデータ情報を検出する (動的なシナリオ) ことにより、テーブル値パラメーターの行セット オブジェクトを作成できます。 この後の各セクションで、これらの 2 つのシナリオについて説明します。  
  
## <a name="static-scenario"></a>静的なシナリオ  
 型情報がわかっている場合、コンシューマーは、テーブル値パラメーターに対応するテーブル値パラメーター行セット オブジェクトをインスタンス化するのに ITableDefinitionWithConstraints::CreateTableWithConstraints を使用します。  
  
 *Guid*フィールド (*pTableID*パラメーター) 特殊な GUID (CLSID_ROWSET_TVP) が含まれています。 *pwszName* メンバーには、コンシューマーがインスタンスを作成するテーブル値パラメーターの型の名前を含めます。 *eKind* フィールドは、DBKIND_GUID_NAME に設定されます。 この名前は、ステートメントがアドホック SQL の場合に必要です。プロシージャ呼び出しの場合、名前は省略可能です。  
  
 コンシューマーでは、集計、 *pUnkOuter* controlling IUnknown のパラメーター。  
  
 テーブル値パラメーターの行セット オブジェクトのプロパティは読み取り専用のため、コンシューマーでは *rgPropertySets* のどのプロパティも設定する必要はありません。  
  
 各 DBCOLUMNDESC 構造体の *rgPropertySets* メンバーの場合、コンシューマーは列ごとに追加のプロパティを指定できます。 これらのプロパティは、DBPROPSET_SQLSERVERCOLUMN プロパティ セットに属しています。 これらのプロパティによって、列ごとに計算の設定と既定の設定を指定できます。 また、NULL 値の許容や ID など、列の既存のプロパティもサポートされます。  
  
 コンシューマーでは、テーブル値パラメーターの行セット オブジェクトから対応する情報を取得するために、IRowsetInfo::GetProperties を使用します。  
  
 計算するには、null、一意、に関する情報を取得し、各列のステータスの更新、コンシューマーは、icolumnsrowset::getcolumnsrowset または icolumnsinfo::getcolumninfo を使用できます。 これらのメソッドでは、各テーブル値パラメーターの行セットの列に関する詳細情報が取得できます。  
  
 コンシューマーは、テーブル値パラメーターの列ごとに型を指定します。 この方法は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でテーブルを作成する際に列を指定する方法と似ています。 コンシューマーが OLE DB ドライバーからを介して SQL Server のテーブル値パラメーター行セット オブジェクトを取得、 *ppRowset*出力パラメーター。  
  
## <a name="dynamic-scenario"></a>動的なシナリオ  
 コンシューマーに型情報がない場合は、テーブル値パラメーター行セット オブジェクトをインスタンス化する iopenrowset::openrowset を使用してください。 すべてのコンシューマーは、プロバイダーに型名を知らせる必要があります。  
  
 このシナリオでは、プロバイダーがコンシューマーに代わって、テーブル値パラメーターの行セット オブジェクトに関する型情報をサーバーから取得します。  
  
 *PTableID*と*pUnkOuter*パラメーターは、静的なシナリオのように設定する必要があります。 その後、OLE DB Driver for SQL Server が型情報 (列情報と制約) をサーバーから取得し、*ppRowset* パラメーターを使用してテーブル値パラメーターの行セット オブジェクトを返します。 この操作にはサーバーとの通信が必要になるため、静的なシナリオよりもパフォーマンスが低くなります。 動的なシナリオは、パラメーター化されたプロシージャ呼び出しでのみ動作します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
