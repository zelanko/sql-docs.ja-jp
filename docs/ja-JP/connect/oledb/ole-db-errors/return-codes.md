---
title: リターン コードの |Microsoft ドキュメント
description: リターン コード
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: bcc47e5e4cdaffc259ae760fd0e1e2073eb9fab6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="return-codes"></a>リターン コード
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  最も基本的なレベルでは、メンバー関数は成功するか失敗するかのどちらかです。 それよりもやや詳細なレベルでは、関数は成功しても、その成功はアプリケーション開発者が意図した状態ではない場合があります。  
  
 OLE DB のリターン コードの詳細については、次を参照してください。[リターン コード (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631)です。  
  
 OLE DB Driver for SQL Server メンバー関数が S_OK を返すときに、関数が成功しました。  
  
 OLE DB Driver for SQL Server メンバー関数が S_OK を返さない、ときに、OLE/COM HRESULT をアンパックする FAILED マクロと IS_ERROR マクロは、全体的な成功または関数の失敗を判断できます。  
  
 FAILED または IS_ERROR が TRUE を返す場合、OLE DB Driver for SQL Server コンシューマーはメンバー関数の実行が失敗したことが保証されます。 FAILED または IS_ERROR を返す場合に FALSE と HRESULT と等しくありません S_OK を OLE DB Driver for SQL Server コンシューマーがその関数はある程度まで成功を保証します。 コンシューマーは、この"success 情報を含む"返された場合は、OLE DB Driver for SQL Server エラー インターフェイスから詳細な情報を取得できます。 また、関数 (、FAILED マクロに TRUE を返します) が失敗した明確にする場合、拡張エラー情報は、OLE DB Driver for SQL Server エラー インターフェイスから利用できます。  
  
 OLE DB Driver for SQL Server コンシューマーは、DB_S_ERRORSOCCURRED により成功が情報"HRESULT 戻り値をよく発生します。 通常、DB_S_ERRORSOCCURRED を返すメンバー関数では、コンシューマーに状態値を提供するパラメーターが 1 つ以上定義されています。 コンシューマーが利用可能なときに、状態の値を取得するアプリケーション ロジックを実装する必要がありますので、状態値パラメーターで返される以外のコンシューマーに使用できる可能性エラー情報はありません。  
  
 メンバー関数の SQL Server OLE DB Driver は、成功コード S_FALSE を返しません。 すべて OLE DB Driver for SQL Server メンバー関数は、常に成功を示すには S_OK を返します。  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
