---
title: sys.fulltext_languages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fulltext_languages
- sys.fulltext_languages_TSQL
- fulltext_languages
- fulltext_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- languages [full-text search]
- sys.fulltext_languages catalog view
ms.assetid: 2ed6b53d-1cf2-4763-9d58-36ea24a610ef
caps.latest.revision: 54
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dabc9334091b5b545c78b069b3e9f31a5a68a1bd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfulltextlanguages-transact-sql"></a>sys.fulltext_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  このカタログ ビューにワード ブレーカーが登録されている言語ごとに 1 行が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 各行には、LCID と言語の名前が表示されます。 言語のワード ブレーカーを登録すると、他の言語リソース (ステミング機能、ノイズ ワード (ストップワード)、および類義語辞典ファイル) をフルテキスト インデックス/クエリ操作で使用できるようになります。 値**名前**または**lcid** 、フルテキスト クエリとフルテキスト インデックスで指定できる[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
   
|列|データ型|Description|  
|------------|---------------|-----------------|  
|**lcid**|**int**|言語の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ロケール識別子 (LCID) です。|  
|**name**|**sysname**|内の別名のいずれかの値は、 [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)の値に対応する**lcid**または LCID の数値の文字列形式。|  
  
## <a name="values-returned-for-default-languages"></a>既定の言語の戻り値  
 次の表に、ワード ブレーカーが既定で登録されている言語の値を示します。  
  
|言語|LCID (LCID)|  
|--------------|----------|  
|アラビア語|1025|  
|ベンガル語 (インド)|1093|  
|英語 (U.K.)|2057|  
|ブルガリア語|1026|  
|カタロニア語|1027|  
|中国語 (中華人民共和国香港特別行政区)|3076|  
|中国語 (中華人民共和国マカオ特別行政区)|5124|  
|中国語 (シンガポール)|4100|  
|クロアチア語|1050|  
|チェコ語|1029|  
|デンマーク語|1030|  
|オランダ語|1043|  
|英語|1033|  
|フランス語|1036|  
|ドイツ語|1031|  
|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ギリシャ語|1032|  
|グジャラート語|1095|  
|ヘブライ語|1037|  
|ヒンディー語|1081|  
|アイスランド語|1039|  
|インドネシア語|1057|  
|イタリア語|1040|  
|日本語|1041|  
|カンナダ語|1099|  
|韓国語|1042|  
|ラトビア語|1062|  
|リトアニア語|1063|  
|マレー語 - マレーシア|1086|  
|マラヤーラム語|1100|  
|マラーティー語|1102|  
|ニュートラル|0|  
|ノルウェー語 (ブークモール)|1044|  
|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ポーランド語|1045|  
|ポルトガル語 (ブラジル)|1046|  
|ポルトガル語 (ポルトガル)|2070|  
|パンジャーブ語|1094|  
|ルーマニア語|1048|  
|ロシア語|1049|  
|セルビア語 (キリル)|3098|  
|セルビア語 (ラテン)|2074|  
|簡体字中国語|2052|  
|スロバキア語|1051|  
|スロベニア語|1060|  
|スペイン語|3082|  
|スウェーデン語|1053|  
|タミール語|1097|  
|テルグ語|1098|  
|タイ語|1054|  
|繁体字中国語|1028|  
|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> トルコ語|1055|  
|ウクライナ語|1058|  
|ウルドゥ語|1056|  
|ベトナム語|1066|  
  
## <a name="remarks"></a>解説  
 更新するには、フルテキスト検索に登録された言語の一覧を使用して[sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**' です。  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [sp_fulltext_load_thesaurus_file &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [構成して、フルテキスト検索の類義語辞典ファイルの管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [構成およびストップ ワードとストップ リストをフルテキスト検索の管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
