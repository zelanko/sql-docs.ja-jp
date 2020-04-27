---
title: WITH CHECK OPTION は、90以降の互換性モードで TOP を含むビューではサポートされていません。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 254969e6201795e2f4ae512e03be26419b71d866
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66090998"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>互換性モード 90 以上では TOP を含むビューで WITH CHECK OPTION がサポートされない
  ビューの SELECT ステートメントまたは参照先のビューで WITH CHECK OPTION と TOP 句を使用するビューを、アップグレード アドバイザーが検出しました。 データベース互換性モードが 80 以下の場合、この方法で定義されたビューを使用してデータを変更することはできますが、正しく実行されず、不正確な結果が生成されることがあります。 ビューまたは参照先のビューで TOP 句を使用し、データベース互換性モードが 90 以上に設定されている場合、WITH CHECK OPTION を使用するビューからデータの挿入や更新を行うことはできません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードすると、ユーザー データベースでは互換性モードが維持されます。 ビューからのデータ変更が必要な場合は、データベース互換性モードを 100 以上に変更する前に WITH CHECK OPTION と TOP の両方を使用するビューを変更してください。 詳細については、「 [sp_dbcmptlevel &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
