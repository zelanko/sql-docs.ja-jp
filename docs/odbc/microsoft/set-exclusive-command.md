---
title: 排他コマンドの設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d140c4be3ab850547ac82f9b954e7313b008dbf0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300862"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE コマンド
テーブル ファイルをネットワーク上で排他用または共有用に開くかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 ネットワーク上で開かれたテーブルのアクセスを、そのテーブルを開いたユーザーに制限します。 このテーブルは、ネットワーク上の他のユーザーがアクセスできません。 また、SET EXCLUSIVE ON は、他のすべてのユーザーが読み取り専用アクセスを持つことを防ぎます。  
  
 OFF  
 (ドライバーの既定値は、Visual FoxPro の既定値は、グローバル データ セッションの場合は ON、プライベート データ セッションではオフです)。ネットワーク上で開かれたテーブルを、ネットワーク上の任意のユーザが共有および変更できるようにします。  
  
## <a name="remarks"></a>解説  
 SET EXCLUSIVE の設定を変更しても、以前に開いたテーブルのステータスは変更されません。 例えば、SET EXCLUSIVE を ON に設定して表をオープンし、後で SET EXCLUSIVE を OFF に変更した場合、その表は排他使用状況を保持します。  
  
## <a name="see-also"></a>参照  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
