---
title: SET EXCLUSIVE Command |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d1a37043d332b54d0d5c5ebb7b2ba9f3acce000
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071759"
---
# <a name="set-exclusive-command"></a>SET EXCLUSIVE コマンド
ネットワーク上でテーブルファイルを排他的に使用するか共有するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 ネットワーク上で開かれているテーブルのアクセシビリティを、そのネットワークを開いたユーザーに制限します。 このテーブルには、ネットワーク上の他のユーザーがアクセスできません。 [排他モードに設定すると、他のすべてのユーザーに読み取り専用アクセスを許可しないようにすることもできます。  
  
 OFF  
 (ドライバーの既定値は、グローバルデータセッションでは Visual FoxPro、プライベートデータセッションでは OFF です)。ネットワーク上で開いているテーブルをネットワーク上の任意のユーザーが共有および変更できるようにします。  
  
## <a name="remarks"></a>解説  
 SET EXCLUSIVE の設定を変更しても、以前に開いたテーブルの状態は変更されません。 たとえば、SET EXCLUSIVE が ON に設定された状態でテーブルを開き、SET EXCLUSIVE を後で OFF に変更した場合、テーブルはその排他使用状態を保持します。  
  
## <a name="see-also"></a>参照  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
