---
title: sys.fulltext_languages (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0aa04b9a4b90b470ca3cc6df4a8f5cf62134027c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68220507"
---
# <a name="sysfulltext_languages-transact-sql"></a>sys.fulltext_languages (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  このカタログ ビューには、ワード ブレーカーに登録されている言語ごとに 1 行が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 各行には、LCID と言語の名前が表示されます。 言語、その他の言語リソースのステミング機能、ノイズ ワード (ストップ ワード)、および類義語辞典のファイルになるのワード ブレーカーの登録時に、フルテキスト インデックス/クエリ操作に使用できます。 値**名前**または**lcid** 、フルテキスト クエリとフルテキスト インデックスで指定できます[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。  
   
|[列]|データ型|説明|  
|------------|---------------|-----------------|  
|**lcid**|**int**|言語の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ロケール識別子 (LCID) です。|  
|**name**|**sysname**|内の別名のいずれかの値は、 [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)の値に対応する**lcid**または LCID の数値の文字列表現。|  
  
## <a name="values-returned-for-default-languages"></a>既定の言語の戻り値  
 次の表に、ワード ブレーカーが既定で登録されている言語の値を示します。  
  
|[言語]|LCID (LCID)|  
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
|簡体中国語|2052|  
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
  
## <a name="remarks"></a>コメント  
 フルテキスト検索に登録された言語の一覧を更新する[sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**'。  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [sp_fulltext_load_thesaurus_file &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [構成して、フルテキスト検索の類義語辞典ファイルを管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
