---
title: "FULLTEXTSERVICEPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FULLTEXTSERVICEPROPERTY_TSQL
- FULLTEXTSERVICEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- FULLTEXTSERVICEPROPERTY function
- services [SQL Server], full-text search properties
- test
ms.assetid: b7dcacb0-af83-4807-9d1e-49148b56b59c
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b40c8cc7070c3cd459cf6fff99854942544f7459
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="fulltextserviceproperty-transact-sql"></a>FULLTEXTSERVICEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Full-Text Engine のプロパティに関する情報を返します。 これらのプロパティを設定しを使用して取得**sp_fulltext_service**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FULLTEXTSERVICEPROPERTY ('property')  
```  
  
## <a name="arguments"></a>引数  
 *プロパティ*  
 フルテキスト サービス レベルのプロパティ名を含む式を指定します。 次の表は、プロパティと、返される情報についての説明の一覧です。  
  
> [!NOTE]  
>  将来のリリースでは、次のプロパティを削除予定[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **ConnectTimeout**、 **DataTimeout**、および**ResourceUsage**です。 新しい開発作業では、これらのプロパティの使用は避け、現在これらのプロパティのいずれかを使用しているアプリケーションは修正するようにしてください。  
  
|プロパティ|値|  
|--------------|-----------|  
|**ResourceUsage**|0 を返します。 旧バージョンとの互換性のためにのみサポートされています。|  
|**ConnectTimeout**|0 を返します。 旧バージョンとの互換性のためにのみサポートされています。|  
|**IsFulltextInstalled**|フルテキスト コンポーネントは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスと共にインストールされます。<br /><br /> 0 = フルテキストはインストールされていない<br /><br /> 1 = フルテキストはインストールされている<br /><br /> NULL = 無効な入力またはエラー。|  
|**DataTimeout**|0 を返します。 旧バージョンとの互換性のためにのみサポートされています。|  
|**LoadOSResources**|オペレーティング システムのワード ブレーカーおよびフィルターが登録されているしのこのインスタンスで使用するかどうかを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 既定では、このプロパティを防ぐための不注意による動作の変更にオペレーティング システム (OS) に加えられた更新プログラムで無効です。 言語のリソースへのアクセスを提供する OS リソースの使用を有効にし、ドキュメントの種類に登録されている[!INCLUDE[msCoName](../../includes/msconame-md.md)]Indexing Service では、それにインスタンス固有のリソースがインストールされているがありません。 OS リソースの読み込みを有効にした場合は、OS リソースが信頼された署名付きバイナリ; であることを確認します。それ以外の場合、読み込みができなくなる場合に**VerifySignature**が 1 に設定します。<br /><br /> 0 = この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス固有のフィルターとワード ブレーカーのみを使用<br /><br /> 1 = OS のフィルターとワード ブレーカーを読み込む|  
|**VerifySignature**|によって、署名付きバイナリのみが読み込まれるかどうかを指定します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search サービス。 既定では、信頼された署名付きバイナリのみが読み込まれます。<br /><br /> 0 を = バイナリが署名付きかどうかを確認できません。<br /><br /> 1 = 信頼された署名付きバイナリのみを確認して読み込む|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="examples"></a>使用例  
 次の例では、署名付きバイナリのみが読み込まれるかどうかを確認し、戻り値は、この検証が行われていないことを示します。  
  
```  
SELECT fulltextserviceproperty('VerifySignature');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
0  
```  
  
 署名の検証をその既定値の 1 に設定する、次を使用できる注`sp_fulltext_service`ステートメント。  
  
```  
EXEC sp_fulltext_service @action='verify_signature', @value=1;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTCATALOGPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)  
  
  

