---
title: テーブル値パラメーターの種類の探索 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 50f79caf7fb6abad0f95415ca42353c43394451d
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39554872"
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コンシューマー: は、クライアント アプリケーションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、OLE DB プロバイダーに、コマンド テキストに指定された場合、各コマンドのパラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーはテーブル値パラメーターの個別の列ごとにメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo でほとんどのパラメーターの型。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、ユーザー定義型および **xml** データ型の導入に伴い、ICommandWithParameters によりユーザー定義型の情報 (名前、スキーマ、およびカタログ) を提供することができなくなったため、GetParameterInfo メソッドは十分に目的を果たしていませんでした。 ISSCommandWithParameters の新しいインターフェイスは、拡張型情報を提供する定義されました。  
  
 テーブル値パラメーターで使用することも ISSCommandWithParameters インターフェイス詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターでの*wType* DBPARAMINFO 構造体のメンバーは、プロバイダーによって DBTYPE_TABLE に設定されます。 DBPARAMINFO 構造体の *ulParamSize* フィールドの値は ~0 です。  
  
 コンシューマーは、次に ISSCommandWithParamters::GetParameterProperties を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求します。  
  
 型名がわかったら、コンシューマーは個々の列情報を取得するために、IOpenRowset::OpenRowset を呼び出すか、テーブル値パラメーターの型名をテーブル名として指定して、DBSCHEMA_TABLE_TYPE_COLUMNS 行セットを取得する必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
