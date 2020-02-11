---
title: 互換性のないアクセス機能 (アクセス機能) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2cc48fa530730beec07aaca4bfb933c9ff8fb2b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67986355"
---
# <a name="incompatible-access-features-accesstosql"></a>互換性のないアクセス機能 (Access Stosql)
Access データベースのすべての機能がと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]互換性があるわけではありません。 たとえば、と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクセスでは、予約されたキーワードのセットが異なります。 これらの問題により、へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の移行が成功することがありません。 移行に関する問題とその対処方法については、次の表を参照してください。  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>移行に影響する可能性のあるデータベースの設定または機能  
  
|Access データベースの設定または機能|移行に関する問題|  
|--------------------------------------|-------------------|  
|Access テーブルには一意のインデックスがありません。|一意のインデックスを持たないテーブルをに移行する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行後にテーブルを変更することはできません。 これにより、アプリケーションの互換性の問題が発生する可能性があります。<br /><br />Access データベースオブジェクトを変換すると、[出力] ウィンドウに、一意のインデックスのない Access テーブルが一覧表示されます。<br /><br />変換時に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルに主キーを追加するようにアクセスを構成できます。 詳細については、「[プロジェクトの設定 (変換)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)」を参照してください。|  
|Access テーブルにはレプリケーション列があります。|レプリケーションシステム列を含む Access テーブルをに移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、移行後に Jet レプリケーション機能が破損します。<br /><br />移行後、データベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]同期されたコピーを維持するには、レプリケーションの使用を検討してください。|  
|一意のインデックスを持つ Access テーブルには、複数の null 値が含まれます。|複数の null 値を持つ一意のインデックスを持つアクセステーブルは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、に転送[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]できません。では、一意のインデックスで複数の null 値が許可されないためです。 これらのテーブルの移行は失敗します。<br /><br />SSMA は、この問題に対して評価レポートでのフラグを作成します。 評価レポートを作成するには、「[変換するアクセスデータベースオブジェクトの評価](assessing-access-database-objects-for-conversion-accesstosql.md)」を参照してください。<br /><br />この問題が存在する場合は、主キーに重複する null 値が含まれていないことを確認する必要があります。 または、複数の null 値を含む主キーまたは一意のインデックスを削除する必要があります。|  
|Access テーブルには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]範囲外の日付値が含まれています。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Datetime**型は、1 Jan 1753 から 31 Dec 9999 の範囲の日付のみを受け取ります。 Access では、1 Jan 100 ~ 31 Dec 9999 の範囲の日付を受け付けます。<br /><br />SSMA は、この問題に対して評価レポートでのフラグを作成します。 評価レポートを作成するには、「[変換するアクセスデータベースオブジェクトの評価](assessing-access-database-objects-for-conversion-accesstosql.md)」を参照してください。<br /><br />SSMA が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]範囲外の日付を解決する方法を構成できます。 詳細については、「[プロジェクトの設定 (移行)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)」を参照してください。|  
|アクセスのインデックス長が900バイトを超えています。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックスでは、インデックスキー列の合計サイズに900バイトの制限があります。 Access テーブルでより大きなインデックスが使用されている場合は、SSMA によって警告が表示されます。<br /><br />データの移行を続行した場合、移行が失敗する可能性があります。|  
|アクセスオブジェクト名は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キーワードであるか、特殊文字を含んでいます。|にアクセス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、さまざまな予約済みキーワードと特殊文字セットを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、キーワードを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]して名前が付けられたオブジェクト、または "select" や "select" などの引用符で囲まれた識別子を使用する場合は、特殊文字を含むオブジェクトを受け入れます。 詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「区切られた識別子 (データベースエンジン)」を参照してください。<br /><br />**注:** 識別子を区切るために引用符を使用するには QUOTED_IDENTIFIER を ON に設定する必要があります。<br /><br />たとえば、 `CREATE TABLE [schema](c1 [FOR])`は、**スキーマ**と**に**予約されているキーワードであっても、有効なステートメントです。 また、 `CREATE TABLE [xxx*yyy](c1 x&y)`テーブルと列の名前に特殊文字** \&#42;** および**&amp;** が含まれている場合でも、は有効なステートメントです。<br /><br />これらのオブジェクトを参照するすべてのクエリでも、角かっこまたは引用符で囲まれた名前を使用する必要があります。 たとえば、クエリ`SELECT * FROM schema`は失敗します。 正しいクエリは次の`SELECT * FROM [schema]`とおりです。<br /><br />Access データベースオブジェクトを変換すると、[出力] ウィンドウに、キーワードまたは特殊文字を使用する Access テーブルが一覧表示されます。 Access のテーブルを変更してから、データベースを削除してから再度追加することができます。または、これらのオブジェクトを参照するクエリを変更して、クエリが識別子を区切るために角かっこまたは引用符を使用するようにすることもできます。 クエリを変更しないと、Access アプリケーションからエラーが返されるか、他の問題が発生する可能性があります。|  
|主キー/外部キーのリレーションシップでは、フィールドのサイズが異なります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、外部キー制約が設定されているデータ型やサイズが異なる列をリンクする Jet 機能はサポートされていません。<br /><br />Access データベースオブジェクトを変換すると、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換されない主キー/外部キーの制約が出力ウィンドウに一覧表示されます。 アクセス列のデータ型とサイズを変更して、access データベースを削除してから再度追加することができます。 または、データを移行することもできますが、で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はこれらの制約は作成されません。|  
|アクセスリレーションシップ内の参照されているテーブルには、主キーと一意のインデックスのいずれもありません。|アクセスは、参照されるテーブルに主キーまたは一意のインデックスがないテーブル間のリレーションシップを受け入れます。 ただし、これはで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はサポートされていません。<br /><br />Access データベースオブジェクトを変換すると、[出力] ウィンドウにはリレーションシップがあり、主キーまたは一意のインデックスがないテーブルが一覧表示されます。 テーブルを変更して主キーまたは一意のインデックスを追加し、Access データベースを削除してから追加し直すことができます。 または、テーブル間のリレーションシップが壊れていても、データを移行できます。|  
|Access テーブルにはハイパーリンク列があります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は**ハイパーリンク**列をサポートしていません。 代わりに、列は Access memo 列と同じように扱われます。 既定では、これらの列は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**nvarchar (max)** 列に変換されます。 マッピングはカスタマイズできます。 詳細については、「[ソースとターゲットのデータ型のマッピング](mapping-source-and-target-data-types-accesstosql.md)」を参照してください。|  
|既定値または検証規則の式には、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure に変換できないアクセス関数が含まれています。|既定の式や検証規則にアクセスするには、アクセスシステム関数、またはに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]マップされていないユーザー定義関数、または SQL Azure します。 または SQL Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]割り当てられていない関数を使用すると、既定の式や検証[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]規則をまたは SQL Azure に読み込むことができなくなります。|  
  
## <a name="see-also"></a>参照  
[Access データベースの移行の準備](preparing-access-databases-for-migration-accesstosql.md)  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
