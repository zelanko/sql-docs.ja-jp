---
title: "テーブル値パラメーターの種類の探索 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 693d5cb8c4e537f44ed5a6ebda788c7e7a38cc5a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コンシューマー-は、クライアント アプリケーションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、コマンド テキストが OLE DB プロバイダーに指定された場合、各コマンド パラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーは、テーブル値パラメーターの各列のメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo によってほとんどのパラメーターの型。 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、ユーザー定義型の導入に伴い、 **xml**データ型、GetParameterInfo メソッドがないこの目的のための十分なため、ユーザー定義型を提供することはできませんでした情報 (名前、スキーマ、およびカタログ) ICommandWithParameters を通じてします。 ISSCommandWithParameters の新しいインターフェイスは、拡張された型情報を提供する定義されました。  
  
 テーブル値パラメーターのも、ISSCommandWithParameters インターフェイスを使用する詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターでの*wType* DBPARAMINFO 構造体のメンバーは、プロバイダーによって DBTYPE_TABLE に設定します。 *UlParamSize* DBPARAMINFO 構造体のフィールドの値を持つ ~ 0 です。  
  
 コンシューマーは ISSCommandWithParamters を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求し、:。GetParameterProperties です。  
  
 型名がわかったら、コンシューマーは、呼び出す必要がありますか、個々 の列情報を取得する IOpenRowset::OpenRowsetor 取得、DBSCHEMA_TABLE_TYPE_COLUMNS 行セット テーブル名とテーブル値パラメーターの型名を指定することによってです。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター (&) #40 です。 OLE DB &#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
