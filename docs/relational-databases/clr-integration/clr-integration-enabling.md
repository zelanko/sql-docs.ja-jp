---
title: CLR 統合を有効にする |マイクロソフトドキュメント
description: CLR をホストする SQL Server は CLR 統合と呼ばれ、既定では無効になっています。 sp_configure ストアド プロシージャを使用して、CLR 統合を有効にします。
ms.custom: ''
ms.date: 09/17/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d161135c8c8b0c7d7932eb08aa98509efc4bc45
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488114"
---
# <a name="clr-integration---enabling"></a>CLR 統合 - 有効化
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  CLR (共通言語ランタイム) 統合機能は既定では無効になっているので、CLR 統合を使用して実装されるオブジェクトを使用するには、この機能を有効にする必要があります。 CLR 統合を有効にするには、 の**ストアド**プロシージャsp_configureの clr [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **enabled**オプションを使用します。  
  
```sql  
EXEC sp_configure 'clr enabled', 1;  
RECONFIGURE;  
GO  
```  
  
 CLR の統合を無効にするには **、clr が有効な**オプションを 0 に設定します。 CLR 統合を無効にすると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ユーザー定義 CLR ルーチンの実行がすべて停止され、すべてのアプリケーション ドメインがアンロードされます。 **階層 ID**データ型、`FORMAT`関数、レプリケーション、ポリシー ベースの管理など、CLR に依存する機能は、この設定の影響を受けず、引き続き機能します。
  
> [!NOTE]  
>  CLR 統合を有効にするには、**システム管理者**および**サーバー管理者**の固定サーバー ロールのメンバーが暗黙的に保持する ALTER SETTINGS サーバー レベルのアクセス許可が必要です。  
  
> [!NOTE]  
>  コンピューターを構成しているメモリ サイズとプロセッサ数が非常に大きい場合、SQL Server の CLR 統合機能をサーバーの起動時に読み込めないことがあります。 この問題に対処するには **、-gmemory_to_reserve**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスの起動オプションを使用してサーバーを起動し、十分な大きさのメモリ値を指定します。 詳細については、「 [データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」を参照してください。  
  
> [!NOTE]  
>  簡易プーリングでは、共通言語ランタイム (CLR) の実行はサポートされていません。 CLR 統合を有効にする前に、簡易プーリングを無効にする必要があります。 詳細については、「 [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sp_configure&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr が有効なサーバー構成オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [トランザクション SQL&#41;&#40;再構成する](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [トランザクション SQL&#41;&#40;グラント](../../t-sql/statements/grant-transact-sql.md)   
 [サーバー レベルの役割](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
