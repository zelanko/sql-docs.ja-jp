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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 373e2c17254b55ed351695286b9a4a5d03f2d47c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420051"
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コンシューマー: は、クライアント アプリケーションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、OLE DB プロバイダーに、コマンド テキストに指定された場合、各コマンドのパラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーは、テーブル値パラメーターの各列のメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo でほとんどのパラメーターの型。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、ユーザー定義型の導入に伴い、 **xml**データ型、GetParameterInfo メソッドは、この目的のための十分なユーザー定義型を指定することでなかったため、情報 (名前、スキーマ、およびカタログ) ICommandWithParameters 経由 ISSCommandWithParameters の新しいインターフェイスは、拡張型情報を提供する定義されました。  
  
 テーブル値パラメーターで使用することも ISSCommandWithParameters インターフェイス詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターでの*wType* DBPARAMINFO 構造体のメンバーは、プロバイダーによって DBTYPE_TABLE に設定されます。 *UlParamSize* DBPARAMINFO 構造体のフィールドの値を持つ ~ 0。  
  
 コンシューマーは ISSCommandWithParamters を使用して追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーター型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求し、:。GetParameterProperties します。  
  
 型名がわかったら、コンシューマーは呼び出す必要がありますか、個々 の列情報を取得する IOpenRowset::OpenRowsetor 取得、DBSCHEMA_TABLE_TYPE_COLUMNS 行セット テーブル名とテーブル値パラメーターの型名を指定することで。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターを使用して、 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
