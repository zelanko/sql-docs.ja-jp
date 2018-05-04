---
title: xp_msver (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs:
- TSQL
helpviewer_keywords:
- xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3ccd27d73c9d318e9bdf76350b15cf845b125602
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="xpmsver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  に関するバージョン情報を返します[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 **xp_msver**もサーバーの実際のビルド番号に関する情報と、サーバー環境に関する情報を返します。 情報を**xp_msver**内で使用できるを返します[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、バッチ、ストアド プロシージャ、およびでは、プラットフォームに依存しないコードのロジックを強化するためにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>引数  
 *optname*  
 オプション名を指定します。次のいずれかの値を指定できます。  
  
|オプション/列名|Description|  
|-------------------------|-----------------|  
|**ProductName**|製品名です。たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**製品バージョン**|製品バージョン。|  
|**言語**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の言語バージョン。|  
|**プラットフォーム**|オペレーティング システム名、製造元の名前、およびチップ ファミリ名を実行しているコンピューターの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**コメント**|その他の情報に関する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**CompanyName**|会社名を生成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corporation します。|  
|**主体**|オペレーティング システム。|  
|**fileVersion**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 実行可能ファイルのバージョン。|  
|**internalName**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] 内部名[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; たとえば、SQLSERVR です。|  
|**LegalCopyright**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に必要な著作権に関する法的情報。例: Copyright© [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corp. 1988-2005.|  
|**LegalTrademarks**|商標に関する法的情報に必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 たとえば、[!INCLUDE[msCoName](../../includes/msconame-md.md)]の登録商標[!INCLUDE[msCoName](../../includes/msconame-md.md)]Corporation します。|  
|**[Originalfilename]**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時に実行されるファイル名。Sqlservr.exe などです。|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**WindowsVersion**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] を実行しているコンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows のバージョン。|  
|**ProcessorCount**|実行しているコンピューターのプロセッサ数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**ProcessorActiveMask**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターに搭載されているプロセッサ。[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows により起動され、使用されます。|  
|**ProcessorType**|プロセッサの種類。 ような**プラットフォーム**です。|  
|**PhysicalMemory**|メガバイト (MB) 単位で実行しているコンピューターにインストールされている RAM の量[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**プロダクト ID**|プロダクト ID (PID) 番号。 インストール中に指定されます。 この番号が元のステッカー上にある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CD ケースです。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 1 (成功)  
  
## <a name="result-sets"></a>結果セット  
 **xp_msver**、任意のパラメーターを指定せず、すべてのオプション値を一覧表示する 4 列の結果セットが返されます。 **xp_msver**、任意のパラメーターを 4 つの列を含む結果セット オプションの値を返します。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [汎用拡張ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
