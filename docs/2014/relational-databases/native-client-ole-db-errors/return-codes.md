---
title: リターンコード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 625d56a38d88b3cccbea1c75ad88917af1a6f6dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63228941"
---
# <a name="return-codes"></a>リターン コード
  最も基本的なレベルでは、メンバー関数は成功するか失敗するかのどちらかです。 それよりもやや詳細なレベルでは、関数は成功しても、その成功はアプリケーション開発者が意図した状態ではない場合があります。  
  
 OLE DB のリターン コードの詳細については、「[リターン コード (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631)」を参照してください。  
  
 Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB プロバイダーのメンバー関数が S_OK を返すと、関数は成功します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのメンバー関数が S_OK を返さない場合、OLE/COM HRESULT 展開に失敗し、IS_ERROR マクロは関数の全体的な成功または失敗を判断できます。  
  
 失敗した場合、または IS_ERROR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が TRUE を返した場合、Native Client OLE DB プロバイダーのコンシューマーは、メンバー関数の実行が失敗したことを保証します。 失敗した場合、または IS_ERROR が FALSE を返し、HRESULT が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] S_OK と一致しない場合、Native Client OLE DB プロバイダーコンシューマーは、何らかの意味で関数が成功したことを保証します。 コンシューマーは、Native Client OLE DB プロバイダーのエラーインターフェイスから、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]この "情報で成功" を返す詳細情報を取得できます。 また、関数が明確に失敗した場合 (失敗したマクロが TRUE を返した場合) は、Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーのエラーインターフェイスから拡張エラー情報を取得できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのコンシューマーは、通常、"情報による成功" という HRESULT を返す DB_S_ERRORSOCCURRED に遭遇します。 通常、DB_S_ERRORSOCCURRED を返すメンバー関数では、コンシューマーに状態値を提供するパラメーターが 1 つ以上定義されています。 コンシューマーは状態値パラメーターに返される情報以外のエラー情報を取得できない場合があるので、状態値が提供された場合にこの値を取得できるアプリケーション ロジックを実装することをお勧めします。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーのメンバー関数は、成功コード S_FALSE を返しません。 すべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の Native Client OLE DB プロバイダーのメンバー関数は、成功を示すために常に S_OK を返します。  
  
## <a name="see-also"></a>参照  
 [エラー](errors.md)  
  
  
