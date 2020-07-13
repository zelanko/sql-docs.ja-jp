---
title: xp_msver (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_msver_TSQL
- xp_msver
dev_langs:
- TSQL
helpviewer_keywords:
- xp_msver
ms.assetid: 9264cf8c-92ba-45ad-b2d6-15d26d805a16
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 995668cb4b36e7086c2777d9cb7cd663e7d33ef4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890757"
---
# <a name="xp_msver-transact-sql"></a>xp_msver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  に関するバージョン情報を返し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 また**xp_msver**は、サーバーの実際のビルド番号とサーバー環境に関する情報も返します。 **Xp_msver**返される情報は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、バッチ、ストアドプロシージャなどで使用して、プラットフォームに依存しないコードのロジックを強化することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_msver [ optname ]  
```  
  
## <a name="arguments"></a>引数  
 *optname*  
 オプション名を指定します。次のいずれかの値を指定できます。  
  
|オプション/列名|説明|  
|-------------------------|-----------------|  
|**同様**|製品名;たとえば、のように [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] なります。|  
|**ProductVersion**|製品のバージョン。|  
|**言語**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の言語バージョン。|  
|**プラットフォーム**|を実行しているコンピューターのオペレーティングシステム名、製造元名、およびチップファミリ名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。|  
|**コメント**|に関するその他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の情報。|  
|**CompanyName**|によって生成される会社名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。たとえば、「Corporation」と指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] します。|  
|**FileDescription**|オペレーティング システム。|  
|**FileVersion**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 実行可能ファイルのバージョン。|  
|**InternalName**|[!INCLUDE[msCoName](../../includes/msconame-md.md)]の内部名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (例: sqlservr.exe)。|  
|**LegalCopyright**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に必要な著作権に関する法的情報。Copyright&#xA9; [!INCLUDE[msCoName](../../includes/msconame-md.md)] Corp. 1988-2005 などです。|  
|**LegalTrademarks**|に必要な法律商標情報 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] は Corporation の登録商標です [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。|  
|**OriginalFilename**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時に実行されるファイル名。Sqlservr.exe などです。|  
|**PrivateBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**SpecialBuild**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**WindowsVersion**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] を実行しているコンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows のバージョン。|  
|**ProcessorCount**|を実行しているコンピューターのプロセッサ数 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。|  
|**ProcessorActiveMask**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターに搭載されているプロセッサ。[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows により起動され、使用されます。|  
|**ProcessorType**|プロセッサの種類。 **プラットフォーム**に似ています。|  
|**PhysicalMemory**|を実行しているコンピューターに搭載されている RAM の容量 (mb 単位) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。|  
|**製品 ID**|プロダクト ID (PID) 番号。 これは、インストール時に指定します。 この番号は、元の CD ケースのステッカーに記載されてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 1 (成功)  
  
## <a name="result-sets"></a>結果セット  
 パラメーターを指定せずに**xp_msver**は、すべてのオプション値を一覧表示する4列の結果セットを返します。 **xp_msver**、任意のパラメーターについて、4列の結果セットをそのオプションの値と共に返します。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>関連項目  
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;の一般的な拡張ストアドプロシージャ](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [@@VERSION &#40;Transact-SQL&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)  
  
  
