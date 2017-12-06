---
title: "互換性のないアクセス機能 (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- Access databases, features incompatible with SQL Azure
- Access databases, features incompatible with SQL Server
- dates
- default expressions
- foreign keys
- hyperlink columns
- incompatible Access features
- indexes
- indexes, length of
- keywords
- primary keys
- reference, incompatible features
- replication columns
- special characters
- unique indexes
- validation rules
ms.assetid: 99d45b9c-e3b9-4d56-8c25-b594b887ace1
caps.latest.revision: "18"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59c6c7d0130c93efb7e5d3136deb0edbd5d05ab9
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="incompatible-access-features-accesstosql"></a>互換性のないアクセス機能 (AccessToSQL)
アクセスするすべてのデータベース機能と互換性のある[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アクセスは、予約済みキーワードの別のセットを持っているとします。 移行を正常に実行を防ぐこれらなどの問題[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 次の表を使用して、詳細については、考えられる移行の問題とそれらについて行うことができます。  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>データベースの設定または機能の移行に影響を与える可能性があります。  
  
|データベースの設定または機能へをアクセスします。|移行の問題|  
|--------------------------------------|-------------------|  
|Access テーブルには、一意のインデックスはありません。|かどうかに、一意のインデックスがないテーブルが移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行後に、テーブルを変更することはできません。 これは、アプリケーションの互換性の問題につながることができます。<br /><br />データベース オブジェクトを変換する場合は、出力ウィンドウは一意のインデックスを持たない任意の Access テーブルを一覧表示します。<br /><br />主キーを追加するアクセスを構成することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換中にテーブルです。 詳細については、次を参照してください。[プロジェクトの設定 (変換)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388)です。|  
|Access テーブルでは、レプリケーションの列があります。|かどうかにレプリケーション システムの列を含むアクセス テーブルが移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Jet レプリケーションの機能が移行後に切断されます。<br /><br />移行後に、使用を検討して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]レプリケーション、データベースの同期されたコピーを維持します。|  
|一意なインデックスのあるアクセス テーブルは、複数の null 値を持ちます。|複数の null 値を持つ一意なインデックスのあるアクセス テーブルを転送できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ためで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、一意のインデックスは、複数の null 値を許可しないようにします。 これらのテーブルの移行は失敗します。<br /><br />SSMA は評価レポートでこの問題にフラグを設定します。 評価レポートを作成するを参照してください。[を評価するデータベース オブジェクトの変換](http://msdn.microsoft.com/en-us/8b9e23d6-da62-437a-8c05-8ad2628b9441)です。<br /><br />この問題が存在する場合は、主キーに重複した null 値がないことを確認する必要があります。 または、主キー列または複数の null 値を含む一意のインデックスを削除する必要があります。|  
|Access テーブルにはうち、日付の値が含まれて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]範囲です。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Datetime**型が 31 年 12 月に 1 の 1753 年 1 月の範囲の日付を受け入れる 9999 のみです。 アクセスを受け入れます 31 年 12 月に 1 年 100年 1 月の範囲の日付から 9999 です。<br /><br />SSMA は評価レポートでこの問題にフラグを設定します。 評価レポートを作成するを参照してください。[を評価するデータベース オブジェクトの変換](http://msdn.microsoft.com/en-us/8b9e23d6-da62-437a-8c05-8ad2628b9441)です。<br /><br />SSMA が日付を解決する方法を構成することができますのうちにある、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]範囲です。 詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d)です。|  
|Access でのインデックスの長さは、900 バイトを超えています。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インデックスには、インデックス キー列の合計サイズ 900 バイトの制限があります。 Access のテーブルより大きなインデックスを使用して、SSMA により、警告が表示されます。<br /><br />データ移行を続行する場合、移行が失敗します。|  
|アクセス オブジェクト名は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]キーワード、または特殊文字を使用します。|アクセスと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]予約済みキーワードと特殊文字のセットは異なります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]使用してという名前のオブジェクトを受け入れる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]キーワードまたは特殊文字"select"など、角かっこや引用符で囲まれた識別子を使用するか、[選択] .p 場合。 詳細については、「区切られた識別子 (データベース エンジン)」を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。<br /><br />**注:**引用符を使用する識別子を区切るため、SET QUOTED_IDENTIFIER が ON をする必要があります。<br /><br />たとえば、`CREATE TABLE [schema](c1 [FOR])`いなくても、有効なステートメントは、**スキーマ**と**の**予約済みキーワードとなっています。 また、`CREATE TABLE [xxx*yyy](c1 x&y)`テーブルと列名に特殊文字が含まれていても、有効なステートメントは、  **\&#42;**と **&amp;**です。<br /><br />それらのオブジェクトを参照するすべてのクエリでは、角かっこまたは引用符と共に名前も使用する必要があります。 たとえば、クエリ`SELECT * FROM schema`は失敗します。 正しいクエリ:`SELECT * FROM [schema]`です。<br /><br />データベース オブジェクトを変換すると、出力ウィンドウはキーワードまたは特殊文字を使用する任意の Access テーブルを一覧表示します。 Access では、テーブルの変更および削除し、データベースをもう一度追加または、クエリでは、識別子を区切るために角かっこまたは引用符を使用できるように、それらのオブジェクトを参照するクエリを変更することができます。 クエリを変更しない場合、アプリケーションにアクセス可能性がありますエラーが返されるまたはその他の問題が発生します。|  
|主キー/外部キーのリレーションシップでは、フィールド サイズが異なります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]異なるデータ型または外部キー制約を使用してサイズを持つ列のリンクの Jet 機能をサポートしません。<br /><br />出力ウィンドウで、主キー/外部キー制約には変換されませんを一覧表示アクセス データベースのオブジェクトを変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 一致すると、および削除し、Access データベースを再度追加できるようにデータ型と列をアクセスでのサイズを変更することができます。 または、データを移行するでこれらの制約は作成されませんが[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|アクセスの関係で参照されるテーブルは、主キーでも、一意のインデックスがあります。|アクセスは、ここで参照されるテーブルが主キーまたは一意のインデックスのテーブル間のリレーションシップを受け入れます。 ただし、これによってサポートされていません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。<br /><br />データベース オブジェクトを変換する場合は、出力ウィンドウにリレーションシップがない主キーまたは一意のインデックスを持つすべてのテーブルが表示されます。 主キーまたは一意のインデックスを追加および削除し、Access データベースを再度追加するテーブルを変更することができます。 または、テーブル間のリレーションシップが壊れているがデータを移行することができます。|  
|ハイパーリンク列があるテーブルにアクセスします。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]サポートしていません**ハイパーリンク**列です。 代わりに、列は、Access メモ列と同様に扱われます。 既定では、これらの列が変換される**nvarchar (max)**内の列[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 マッピングをカスタマイズすることができます。 詳細については、次を参照してください。[マッピング ソースとターゲットのデータ型](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)です。|  
|既定または検証ルール式に変換できません。 アクセス関数が含まれて[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。|アクセス システム関数またはユーザー定義関数にマップされていないアクセス既定式や検証規則を含めることがあります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 マップされていない関数を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の防止が既定の式またはに検証規則を読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。|  
  
## <a name="see-also"></a>参照  
[Access データベースの移行の準備](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
