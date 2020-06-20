---
title: 0xFFFF 文字はオブジェクト識別子として有効ではありません |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4594c1cca0fc183100d927842cc2b533694bf90e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85046156"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>0xFFFF 文字はオブジェクト識別子としては無効である
  アップグレード アドバイザーによって、オブジェクト識別子に 0xFFFF 文字が検出されました。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、データベース、テーブル、列などのオブジェクトの識別子にこの文字が含まれていると、データベース互換性モードが 90 以上に設定されている場合にオブジェクトを参照したりオブジェクトの名前を変更することができません。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] にアップグレードすると、ユーザー データベースでは互換性モードが維持されます。 データベース互換性モードを 90 以上に変更する前に、0xFFFF 文字を含むオブジェクトの名前を変更します。  
  
 識別子の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「識別子」を参照してください。 データベース互換性モードの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
