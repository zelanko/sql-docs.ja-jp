---
title: Irowsetfastload::commit (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553f3aaaceae23944ae9b2d0be7d8129a22c0dd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084540"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルに書き込みます。 サンプルについては、次を参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md)と[SQL SERVER を使用して IROWSETFASTLOAD と ISEQUENTIALSTREAM に BLOB データを送信&#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *fDone*[in]  
 FALSE の場合、行セットは有効なまま保持され、コンシューマーはこの行セットを使用してさらに行を挿入できます。 TRUE の場合、行セットは無効になり、コンシューマーはこれ以上行を挿入できません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功し、挿入されたすべてのデータが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに書き込まれました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。 特定のエラー テキストのエラー情報をプロバイダーから取得してください。  
  
 E_UNEXPECTED  
 によって以前に無効に一括コピー行セットに対してメソッドが呼び出された、 **irowsetfastload::commit**メソッドです。  
  
## <a name="remarks"></a>コメント  
 A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー行セットは、遅延更新モードの行セットとして動作します。 保留中の挿入、行セットをサポートするのに挿入された行が同じ方法で扱われるように、行セットから行のデータを挿入すると、 **IRowsetUpdate**です。  
  
 コンシューマーは、呼び出す必要があります、**コミット**書き込む挿入された行を一括コピー行セットのメソッド、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と同じ方法でテーブル、 **irowsetupdate::update**メソッドを使用して、保留中の行を送信、SQL Server のインスタンス。  
  
 コンシューマーに呼び出さずに一括コピー行セットの参照を解放する場合、**コミット**メソッド、すべての挿入されたなかった書き込まれた行は失われます。  
  
 コンシューマーは、挿入された行をバッチ処理を呼び出して、**コミット**メソッドを*fDone*引数が FALSE に設定します。 ときに*fDone*が TRUE に設定すると、行セットは無効になります。 無効な一括コピー行セットのみをサポート、 **ISupportErrorInfo**インターフェイスと**irowsetfastload::release**メソッドです。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  