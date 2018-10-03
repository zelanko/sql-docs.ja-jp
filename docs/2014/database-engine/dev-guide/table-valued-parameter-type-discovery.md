---
title: テーブル値パラメーターの種類の探索 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66f2be8633c7070e2458d5c1e1258fe3bcb9f949
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146722"
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
  コンシューマー: は、クライアント アプリケーションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、OLE DB プロバイダーに、コマンド テキストに指定された場合、各コマンドのパラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーはテーブル値パラメーターの個別の列ごとにメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo でほとんどのパラメーターの型。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、ユーザー定義型の導入に伴い、`xml`データ型、GetParameterInfo メソッドは、この目的のための十分なユーザー定義型の情報を提供することでなかったため、(名前、スキーマ、およびICommandWithParameters 経由のカタログ)。 ISSCommandWithParameters の新しいインターフェイスは、拡張型情報を提供する定義されました。  
  
 テーブル値パラメーターで使用することも ISSCommandWithParameters インターフェイス詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターでの*wType* DBPARAMINFO 構造体のメンバーは、プロバイダーによって DBTYPE_TABLE に設定されます。 DBPARAMINFO 構造体の *ulParamSize* フィールドの値は ~0 です。  
  
 コンシューマーは、次に ISSCommandWithParamters::GetParameterProperties を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求します。  
  
 型名がわかったら、コンシューマーは個々の列情報を取得するために、IOpenRowset::OpenRowset を呼び出すか、テーブル値パラメーターの型名をテーブル名として指定して、DBSCHEMA_TABLE_TYPE_COLUMNS 行セットを取得する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
