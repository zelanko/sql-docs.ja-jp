---
title: "RECONFIGURE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/20/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RECONFIGURE
- RECONFIGURE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- reconfiguring configuration options
- configuration options [SQL Server], reconfiguring
- updating configuration options
- RECONFIGURE, RECONFIGURE statement
- RECONFIGURE
- RECONFIGURE, WITH OVERRIDE statement
ms.assetid: 2e6e4eeb-b70b-4f45-a253-28ac4e595d75
caps.latest.revision: "50"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 80e8f951e053441b15716c8fc1f8c79abbe026b9
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="reconfigure-transact-sql"></a>RECONFIGURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在構成されている値を更新 (、 **config_value**内の列、 **sp_configure**結果セット) では、構成オプションの変更、 **sp_configure**システムストアド プロシージャです。 RECONFIGURE が現在実行中の値を常に更新していない一部の構成オプションは、サーバーの停止と再起動を現在実行中の値を更新する必要があるため (、 **run_value**内の列、 **sp_configure**結果セット) の変更された構成値。    
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>構文    
    
```    
    
RECONFIGURE [ WITH OVERRIDE ]    
```    
    
## <a name="arguments"></a>引数    
 RECONFIGURE    
 構成の設定でサーバーの停止と再起動を必要としない場合、現在実行中の値を更新することを指定します。 また、RECONFIGURE は無効な値のいずれかの新しい構成値を確認 (など、並べ替え順序の値に存在しない**syscharsets**) や非推奨値。 構成オプションでサーバーの停止と再起動を必要としない場合、RECONFIGURE を指定すると、構成オプションに関する現在実行中の値と現在の構成値は同じになります。    
    
 WITH OVERRIDE    
 構成値のための (無効な値や非推奨値) のチェックを無効になります、**復旧間隔**詳細構成オプション。    
    
 ただし、いくつかに致命的なエラーは回避も、WITH OVERRIDE オプションを使用して、ほとんどの構成オプションを再構成できます。 たとえば、**最小サーバー メモリ**で指定された値より大きい値を持つ構成オプションを構成することはできません、**サーバー メモリの最大**構成オプション。
      
## <a name="remarks"></a>解説    
 **sp_configure**は新しい構成オプションごとに文書化されている有効な範囲外の構成オプションの値を受け入れません。    
    
 RECONFIGURE は、明示的または暗黙的なトランザクションでは使用できません。 複数のオプションを同時に再構成すると、いずれかの再構成オプションが失敗した場合に、すべての再構成オプションが無効になります。    
    
 リソース ガバナーを再構成する際にの再構成オプションを参照してください[ALTER RESOURCE GOVERNOR &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/alter-resource-governor-transact-sql.md)。    
    
## <a name="permissions"></a>権限    
 RECONFIGURE 権限は、既定では ALTER SETTINGS 権限が与えられているユーザーに与えられます。 **Sysadmin**と**serveradmin**固定サーバー ロールが暗黙的にこのアクセス許可を保持します。    
    
## <a name="examples"></a>使用例    
 次の例の数の上限を設定する、`recovery interval`構成オプションを`75`時間 (分) を使用して`RECONFIGURE WITH OVERRIDE`をインストールします。 60 分より長い復旧間隔は推奨されず、既定では許可されせんが、 `WITH OVERRIDE` オプションが指定されているので、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では指定の値 (`90`) が `recovery interval` 構成オプションに対して有効かどうかはチェックされません。    
    
```    
EXEC sp_configure 'recovery interval', 75'    
RECONFIGURE WITH OVERRIDE;    
GO    
```    
    
## <a name="see-also"></a>参照    
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)     
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)    
    
  
