---
title: テーブル値パラメーターの種類の探索 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 021109d32ceed7055348aea0bb0cb9ac32a4c7c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231952"
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
  コンシューマー: は、クライアント アプリケーションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、OLE DB プロバイダーに、コマンド テキストに指定された場合、各コマンドのパラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーは、テーブル値パラメーターの各列のメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo でほとんどのパラメーターの型。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、ユーザー定義型の導入に伴い、`xml`データ型、GetParameterInfo メソッドは、この目的のための十分なユーザー定義型の情報を提供することでなかったため、(名前、スキーマ、およびICommandWithParameters 経由のカタログ)。 ISSCommandWithParameters の新しいインターフェイスは、拡張型情報を提供する定義されました。  
  
 テーブル値パラメーターで使用することも ISSCommandWithParameters インターフェイス詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターでの*wType* DBPARAMINFO 構造体のメンバーは、プロバイダーによって DBTYPE_TABLE に設定されます。 *UlParamSize* DBPARAMINFO 構造体のフィールドの値を持つ ~ 0。  
  
 コンシューマーは ISSCommandWithParamters を使用して追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーター型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求し、:。GetParameterProperties します。  
  
 型名がわかったら、コンシューマーは呼び出す必要がありますか、個々 の列情報を取得する IOpenRowset::OpenRowsetor 取得、DBSCHEMA_TABLE_TYPE_COLUMNS 行セット テーブル名とテーブル値パラメーターの型名を指定することで。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターを使用して、 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
