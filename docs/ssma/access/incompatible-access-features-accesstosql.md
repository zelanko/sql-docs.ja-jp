---
title: 互換性のない Access の機能 (AccessToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a30e18e9de8431dc40099fc87cf37e636f24f98c
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980544"
---
# <a name="incompatible-access-features-accesstosql"></a>互換性のない Access の機能 (AccessToSQL)
アクセスするすべてのデータベース機能と互換性のある[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]アクセスは、予約済みキーワードの別のセットを持っているとします。 これらへの移行を成功を防ぐことができますなどの問題[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。 次の表を使用して、考えられる移行の問題とそれらについて何ができるについて説明します。  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>データベースの設定または機能の移行に影響を与える可能性があります。  
  
|データベースの設定や機能へをアクセスします。|移行の問題|  
|--------------------------------------|-------------------|  
|テーブルにアクセスするには、一意のインデックスはありません。|一意のインデックスがないテーブルに移行されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行後に、テーブルを変更することはできません。 これは、アプリケーション互換性の問題につながります。<br /><br />Access データベース オブジェクトを変換するときに、出力ウィンドウには一意のインデックスがない Access のテーブルが表示されます。<br /><br />プライマリ キーを追加するアクセスを構成することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]変換中にテーブルです。 詳細については、次を参照してください。[プロジェクトの設定 (変換)](http://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)します。|  
|テーブルにアクセスするには、レプリケーションの列があります。|レプリケーション システム列を含む Access テーブルに移行されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Jet のレプリケーション機能は移行後に中断されます。<br /><br />移行後に、使用を検討して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]レプリケーション、データベースの同期コピーを維持するためにします。|  
|一意インデックスがテーブルにアクセスでは、複数の null 値が含まれます。|複数の null 値を含む一意のインデックスがテーブルにアクセスを転送できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ためで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、一意のインデックスは、複数の null 値を許可しないようにします。 これらのテーブルの移行は失敗します。<br /><br />SSMA は評価レポートには、この問題にフラグを設定します。 評価レポートを作成するを参照してください。[変換のための Access データベース オブジェクトの評価](http://msdn.microsoft.com/8b9e23d6-da62-437a-8c05-8ad2628b9441)します。<br /><br />この問題が存在する場合は、主キーに重複する null 値がないことを確認する必要があります。 または、プライマリ キーまたは複数の null 値を含む一意のインデックスを削除する必要があります。|  
|テーブルにアクセスするの日付の値が含まれて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]範囲。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **Datetime**型が 1 年 1753年 1 月年 12 月の 31 の範囲内の日付を受け入れる 9999 のみです。 アクセスが 31 の 10 進数に 1 年 100年 1 月の範囲の日付を受け入れる 9999 です。<br /><br />SSMA は評価レポートには、この問題にフラグを設定します。 評価レポートを作成するを参照してください。[変換のための Access データベース オブジェクトの評価](http://msdn.microsoft.com/8b9e23d6-da62-437a-8c05-8ad2628b9441)します。<br /><br />SSMA で日付がどのように解決する方法を構成するは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]範囲。 詳細については、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)します。|  
|Access でのインデックスの長さは、900 バイトを超えます。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インデックスでは、インデックス キー列の合計サイズ 900 バイト制限があります。 テーブルにアクセスするより大きなインデックスを使用して、SSMA で警告が表示されます。<br /><br />データ移行を続行した場合、移行が失敗します。|  
|オブジェクト名のアクセスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]キーワード、または特殊文字を含めます。|アクセスと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]予約済みキーワードと特殊文字のセットは異なります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 使用してという名前のオブジェクトが受け入れる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]キーワードまたは"select"などの角かっこや引用符で囲まれた識別子を使用するか、または [select] .p 場合特殊文字を含めます。 詳細については、「区切り記号 Identifiers (データベース エンジン)」を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブックの「します。<br /><br />**注:** 識別子を区切る引用符を使用する、SET QUOTED_IDENTIFIER が ON をする必要があります。<br /><br />たとえば、`CREATE TABLE [schema](c1 [FOR])`されていなくても、有効なステートメントを**スキーマ**と**の**は予約済みキーワード。 また、`CREATE TABLE [xxx*yyy](c1 x&y)`有効なステートメントは、テーブルと列名に特殊文字が含まれているにもかかわらず、 **\&#42;** と**&amp;** します。<br /><br />これらのオブジェクトを参照するすべてのクエリでは、角かっこまたは引用符、名前を使用する必要があります。 たとえば、クエリ`SELECT * FROM schema`は失敗します。 適切なクエリ:`SELECT * FROM [schema]`します。<br /><br />Access データベース オブジェクトを変換するときに、出力ウィンドウはキーワードまたは特殊文字を使用するアクセス テーブルを一覧表示します。 Access では、テーブルの変更し削除し、もう一度データベースを追加または、クエリの識別子を区切るために角かっこまたは引用符を使用できるように、これらのオブジェクトを参照するクエリを変更することができます。 場合は、クエリを変更しないでください、アプリケーションにアクセス可能性がありますエラーが返されるまたはその他の問題が発生します。|  
|フィールド サイズは、主キー/外部キーのリレーションシップによって異なります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 異なるデータ型または外部キー制約を使用してサイズを持つ列のリンクの Jet 機能をサポートしません。<br /><br />出力ウィンドウで、主キー/外部キー制約に変換を一覧表示 Access データベース オブジェクトを変換するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。 一致すると、削除および Access データベースを再度追加できるように、データ型とアクセスの列のサイズを変更できます。 または、データを移行するでこれらの制約は作成されませんが[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。|  
|アクセスの関係で参照されるテーブルは、主キーも一意のインデックスがあります。|アクセスは、参照先のテーブルにありませんが、主キーまたは一意のインデックス テーブル間のリレーションシップを受け入れます。 ただし、これでサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。<br /><br />Access データベース オブジェクトを変換するときに、出力ウィンドウにリレーションシップがありません主キーまたは一意のインデックスを持つすべてのテーブルが表示されます。 主キーまたは一意のインデックスを追加し、削除して、Access データベースを再度追加するテーブルを変更することができます。 または、テーブル間のリレーションシップが切断されますが、データを移行することができます。|  
|テーブルにアクセスするには、ハイパーリンク列があります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] サポートしていません**ハイパーリンク**列。 代わりに、列はメモ列のアクセスのように扱われます。 既定では、これらの列が変換される**nvarchar (max)** 列[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。 マッピングをカスタマイズすることができます。 詳細については、次を参照してください。[マッピング ソースとターゲットのデータ型](http://msdn.microsoft.com/b362a075-16e7-423f-b63f-e1e9f02844a9)します。|  
|既定値または検証規則式に変換できません。 アクセス関数を含めることが[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。|アクセス システム関数またはユーザー定義関数にマップされていないアクセスの既定の式または検証規則を含めることがあります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 マップされていない関数を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の防止、既定の式またはに検証規則を読み込んでから[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。|  
  
## <a name="see-also"></a>参照  
[Access データベースの移行の準備](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
