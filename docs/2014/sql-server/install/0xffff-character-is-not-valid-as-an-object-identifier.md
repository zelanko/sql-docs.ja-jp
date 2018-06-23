---
title: 0 xffff 文字はオブジェクト識別子として有効ではありません |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ded2cd54bced9ae69e207a1b609688c2fcf3b633
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085132"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>0xFFFF 文字はオブジェクト識別子としては無効である
  アップグレード アドバイザーによって、オブジェクト識別子に 0xFFFF 文字が検出されました。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、データベース、テーブル、列などのオブジェクトの識別子にこの文字が含まれていると、データベース互換性モードが 90 以上に設定されている場合にオブジェクトを参照したりオブジェクトの名前を変更することができません。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] にアップグレードすると、ユーザー データベースでは互換性モードが維持されます。 データベース互換性モードを 90 以上に変更する前に、0xFFFF 文字を含むオブジェクトの名前を変更します。  
  
 識別子の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「識別子」を参照してください。 データベース互換性モードの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
