---
title: テーブル値パラメーターの種類の探索 |Microsoft Docs
description: テーブル値パラメーターの種類を使用した検出 OLE DB Driver for SQL Server
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
- table-valued parameters, type discovery
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 5c3d384f09f362bfca42882988a559608cc493c4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026724"
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  コンシューマー、つまり OLE DB Driver for SQL Server を使用するクライアント アプリケーションでは、コマンド テキストが OLE DB プロバイダーに提供されている場合は、各コマンド パラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーはテーブル値パラメーターの個別の列ごとにメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo でほとんどのパラメーターの型。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降では、ユーザー定義型および **xml** データ型の導入に伴い、ICommandWithParameters によりユーザー定義型の情報 (名前、スキーマ、およびカタログ) を提供することができなくなったため、GetParameterInfo メソッドは十分に目的を果たしていませんでした。 ISSCommandWithParameters の新しいインターフェイスは、拡張型情報を提供する定義されました。  
  
 テーブル値パラメーターで使用することも ISSCommandWithParameters インターフェイス詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターでは、DBPARAMINFO 構造体の *wType* メンバーが、プロバイダーによって DBTYPE_TABLE に設定されます。 DBPARAMINFO 構造体の *ulParamSize* フィールドの値は ~0 です。  
  
 コンシューマーは、次に ISSCommandWithParamters::GetParameterProperties を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求します。  
  
 型名がわかったら、コンシューマーは個々の列情報を取得するために、IOpenRowset::OpenRowset を呼び出すか、テーブル値パラメーターの型名をテーブル名として指定して、DBSCHEMA_TABLE_TYPE_COLUMNS 行セットを取得する必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
