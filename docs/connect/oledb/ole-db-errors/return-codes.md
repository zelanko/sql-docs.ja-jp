---
title: リターン コード |Microsoft Docs
description: リターン コード
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
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
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 7bb86d9e9c43b6d8c73f8018e80eebd5a0a54f5e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786062"
---
# <a name="return-codes"></a>リターン コード
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  最も基本的なレベルでは、メンバー関数は成功するか失敗するかのどちらかです。 それよりもやや詳細なレベルでは、関数は成功しても、その成功はアプリケーション開発者が意図した状態ではない場合があります。  
  
 OLE DB のリターン コードの詳細については、「[リターン コード (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631)」を参照してください。  
  
 OLE DB Driver for SQL Server メンバー関数が S_OK を返すときに、関数が成功しました。  
  
 OLE DB Driver for SQL Server のメンバー関数が S_OK を返さない場合は、OLE/COM HRESULT をアンパックする FAILED マクロと IS_ERROR マクロにより、関数全体が成功したか失敗したかを判断できます。  
  
 FAILED または IS_ERROR が TRUE を返した場合、OLE DB Driver for SQL Server のコンシューマーは、メンバー関数の実行が失敗したことを確認できます。 FAILED または IS_ERROR が返される場合は、FALSE と HRESULT と S_OK を OLE DB Driver for SQL Server コンシューマーがその関数はある意味で成功を保証が等しくないです。 コンシューマーは OLE DB Driver for SQL Server のエラー インターフェイスから返される、関数の成功に関する詳細情報を取得できます。 また、関数が明らかに失敗している (FAILED マクロが TRUE を返した) 場合、OLE DB Driver for SQL Server のエラー インターフェイスから拡張エラー情報を取得できます。  
  
 OLE DB Driver for SQL Server コンシューマーは、情報を含む DB_S_ERRORSOCCURRED"success"HRESULT 戻り値をよく遭遇します。 通常、DB_S_ERRORSOCCURRED を返すメンバー関数では、コンシューマーに状態値を提供するパラメーターが 1 つ以上定義されています。 コンシューマーは状態値パラメーターに返される情報以外のエラー情報を取得できない場合があるので、状態値が提供された場合にこの値を取得できるアプリケーション ロジックを実装することをお勧めします。  
  
 OLE DB Driver for SQL Server メンバー関数は、成功コード S_FALSE を返しません。 すべて OLE DB Driver for SQL Server メンバー関数は、常に成功した場合は S_OK を返します。  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
