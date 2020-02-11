---
title: テーブル値パラメーターの型の検出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf3f7b4d6754902ac38172ffa0e8fc392599d307
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62780321"
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
  コンシューマー (つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用するクライアントアプリケーション) は、コマンドテキストが OLE DB プロバイダーに与えられていれば、各コマンドパラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーはテーブル値パラメーターの個別の列ごとにメタデータ情報を検出できます。  
  
 プロシージャパラメーターの型情報は、ほとんどのパラメーターの型に対して ICommandWithParameters:: GetParameterInfo でサポートされています。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]は、ユーザー定義型と`xml`データ型の導入により、Getparameterinfo メソッドは、ICommandWithParameters を介してユーザー定義型情報 (名前、スキーマ、およびカタログ) を提供できなかったため、この目的には不十分でした。 拡張型情報を提供するために、ISSCommandWithParameters という新しいインターフェイスが定義されました。  
  
 テーブル値パラメーターの場合は、ISSCommandWithParameters インターフェイスを使用して詳細情報を検出することもできます。 クライアントは、コマンドオブジェクトを準備した後で ISSCommandWithParameters:: GetParameterInfo を呼び出します。 テーブル値パラメーターでは、DBPARAMINFO 構造体の *wType* メンバーが、プロバイダーによって DBTYPE_TABLE に設定されます。 DBPARAMINFO 構造体の *ulParamSize* フィールドの値は ~0 です。  
  
 コンシューマーは、次に ISSCommandWithParameters::GetParameterProperties を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求します。  
  
 型名がわかったら、コンシューマーは個々の列情報を取得するために、IOpenRowset::OpenRowset を呼び出すか、テーブル値パラメーターの型名をテーブル名として指定して、DBSCHEMA_TABLE_TYPE_COLUMNS 行セットを取得する必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
