---
title: PUBLISHINGSERVERNAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 178b2cfddf2d7029e731726025d5d47793b37305
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37782793"
---
# <a name="replication-functions---publishingservername"></a>レプリケーション関数 - PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース ミラーリング セッションに参加している、パブリッシュされたデータベースの発行元パブリッシャーの名前を返します。 この関数は、パブリケーション データベース上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパブリッシャー インスタンス側で実行されます。 パブリッシュされたデータベースの元のパブリッシャーを特定するときに使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 PUBLISHINGSERVERNAME は、すべての種類のレプリケーションで使用できます。  
  
 PUBLISHINGSERVERNAME は、パブリッシャーとミラーリング パートナー インスタンスの間のパブリケーション データベースでデータベース ミラーリング セッションが開かれているときに使用します。  
  
 この関数は、パブリケーション データベースのコンテキストで実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のミラーリング サーバー インスタンスのパブリケーション データベースで PUBLISHINGSERVERNAME を実行すると、パブリッシュされたデータベースの発行元パブリッシャー インスタンスの名前が返されます。 パブリッシュされていないミラーリング サーバー インスタンスのデータベース、またはフェールオーバー後にミラーリング サーバー インスタンスからパブリッシュされたミラーリング サーバー インスタンスのデータベースでこの関数を実行すると、ミラーリング サーバー インスタンスの名前が返されます。 元のパブリッシャー インスタンスでこの関数を実行すると、パブリッシャーの名前が返されます。  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [レプリケーションの動作 (&) #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
