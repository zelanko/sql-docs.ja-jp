---
title: リターン コード | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09056c9d4964ad10b2b25f63ef5991a1a7742cab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301030"
---
# <a name="return-codes"></a>リターン コード
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  最も基本的なレベルでは、メンバー関数は成功するか失敗するかのどちらかです。 それよりもやや詳細なレベルでは、関数は成功しても、その成功はアプリケーション開発者が意図した状態ではない場合があります。  
  
 OLE DB のリターン コードの詳細については、「[リターン コード (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーのメンバー関数がS_OK返すとき、関数は成功しました。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーのメンバー関数がS_OKを返さない場合、OLE/COM HRESULT アンパック失敗およびIS_ERROR マクロは、関数の全体的な成功または失敗を決定できます。  
  
 FAILED またはIS_ERRORが TRUE[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を返した場合、ネイティブ クライアント OLE DB プロバイダー コンシューマーは、メンバー関数の実行が失敗したことを保証します。 失敗またはIS_ERRORが FALSE を返し、HRESULT がS_OK[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と等しくない場合、ネイティブ クライアント OLE DB プロバイダー コンシューマーは、関数が何らかの意味で成功したことを保証します。 コンシューマは、ネイティブ クライアントの OLE DB プロバイダ エラー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インターフェイスから、この "成功した情報" の返しに関する詳細情報を取得できます。 また、関数が明確に失敗した場合 (FAILED マクロが TRUE を返す)、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張エラー情報はネイティブ クライアント OLE DB プロバイダーのエラー インターフェイスから取得できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダー コンシューマーは、一般的に"情報を使用して成功" HRESULT を返すDB_S_ERRORSOCCURREDに遭遇します。 通常、DB_S_ERRORSOCCURRED を返すメンバー関数では、コンシューマーに状態値を提供するパラメーターが 1 つ以上定義されています。 コンシューマーは状態値パラメーターに返される情報以外のエラー情報を取得できない場合があるので、状態値が提供された場合にこの値を取得できるアプリケーション ロジックを実装することをお勧めします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーのメンバー関数は、S_FALSE成功コードを返しません。 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーのメンバー関数はすべて、常に成功を示すS_OK返します。  
  
## <a name="see-also"></a>参照  
 [エラー](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
