---
title: Irowsetfastload::commit (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 745282c1d1e8fa36c9d0a407ac32171304d05197
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417171"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルに書き込みます。 サンプルについては、次を参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md)と[BLOB データを SQL SERVER を使用して IROWSETFASTLOAD と ISEQUENTIALSTREAM を送信&#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)します。  
  
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
 によって以前に無効にする一括コピー行セットに対してメソッドが呼び出された、 **irowsetfastload::commit**メソッド。  
  
## <a name="remarks"></a>コメント  
 A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー行セットは、遅延更新モードの行セットとして動作します。 挿入行セットのサポートに保留中に挿入された行が同じ方法で扱われるように、ユーザーは、行セットを使用して行データを挿入、 **IRowsetUpdate**します。  
  
 コンシューマーを呼び出す必要があります、**コミット**メソッドに挿入された行を記述する一括コピー行セットを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルと同じ方法で、 **irowsetupdate::update**メソッドを使用すると、保留中の行を送信します。SQL Server のインスタンス。  
  
 コンシューマーに呼び出さずに一括コピー行セットの参照を解放する場合、**コミット**メソッドでは、すべての挿入されたいなかった書き込まれた行は失われます。  
  
 コンシューマーは、挿入された行をバッチ処理を呼び出して、**コミット**メソッドを*fDone*引数が FALSE に設定します。 ときに*fDone*が TRUE に設定すると、行セットは無効になります。 無効な一括コピーの行セットのみをサポート、 **ISupportErrorInfo**インターフェイスと**irowsetfastload::release**メソッド。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
