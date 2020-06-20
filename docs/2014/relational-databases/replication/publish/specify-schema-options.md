---
title: スキーマ オプションの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85005240"
---
# <a name="specify-schema-options"></a>スキーマ オプションの指定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、スキーマのオプションを指定する方法について説明します。 テーブルまたはビューをパブリッシュするとき、パブリッシュされたオブジェクト用にレプリケートされるオブジェクトの作成オプションを制御できます。 アーティクルが作成されるときにこれらのオプションを設定することができ、後で変更することもできます。 アーティクルに対してオプションを明示的に指定しなかった場合、既定のオプションが定義されます。  
  
> [!NOTE]  
>  レプリケーションのストアド プロシージャを使用した場合の既定のスキーマ オプションは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]を使ってアーティクルを追加するときの既定のオプションとは異なる場合があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Recommendations (推奨事項)](#Recommendations)  
  
-   **スキーマ オプションを指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションの作成後にスキーマ オプションを変更する場合は、新しいスナップショットを生成する必要があります。  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> 推奨事項  
  
-   スキーマオプションの完全な一覧については、 [sp_addarticle &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)の** \@ schema_option**パラメーターと sp_addmergearticle &#40;[transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を参照してください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 [**アーティクルのプロパティ- \<Article> ** ] ダイアログボックスの [**プロパティ**] タブで、制約やトリガーをサブスクライバーにコピーするかどうかなど、スキーマオプションを指定します。 このタブは、パブリケーションの新規作成ウィザードおよび [**パブリケーションのプロパティ \<Publication> -** ] ダイアログボックスで使用できます。 ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
#### <a name="to-specify-schema-options"></a>スキーマ オプションを指定するには  
  
1.  パブリケーションの新規作成ウィザードまたは [パブリケーションの**プロパティ- \<Publication> ** ] ダイアログボックスの [**アーティクル**] ページで、アーティクルを選択し、[**アーティクルのプロパティ**] をクリックします。  
  
2.  スキーマ オプションの変更を適用するアーティクルを選択します。  
  
    -   [**反転表示された \<ObjectType> アーティクルのプロパティを設定**] をクリックして [アーティクルの** \<ObjectName> プロパティ-** ] ダイアログボックスを開きます。このダイアログボックスで行われたプロパティの変更は、[**アーティクル**] ページのオブジェクトペインで強調表示されているオブジェクトにのみ適用されます。  
  
    -   [すべて**の \<ObjectType> アーティクルの**プロパティを設定] をクリックして [**すべての \<ObjectType> アーティクル**のプロパティ] ダイアログボックスを開きます。このダイアログボックスで行われたプロパティの変更は、[**アーティクル**] ページの [オブジェクト] ペインで、まだパブリケーション用に選択されていないものも含めて、その種類のすべてのオブジェクトに適用されます。  
  
        > [!NOTE]  
        >  [**すべての \<ObjectType> アーティクルのプロパティ**] ダイアログボックスで行われたプロパティの変更は、[**アーティクル \<ObjectName> のプロパティ-** ] ダイアログボックスで以前に行われたものよりも優先されます。 たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。 次に、それぞれのオブジェクトに対してプロパティを設定します。  
  
3.  [**アーティクルの \<Article> プロパティ-** ] ダイアログボックスの [**プロパティ**] タブで、[**オブジェクトと設定をサブスクライバーにコピー**して、そのオブジェクトをサブスクライバーおよび**対象オブジェクト**にコピーする] セクションで、オプションの値を指定します。  
  
4.  必要に応じてプロパティを変更し、 **[OK]** をクリックします。  
  
5.  [**パブリケーションのプロパティ- \<Publication> ** ] ダイアログボックスが表示されている場合は、[ **OK** ] をクリックして保存し、ダイアログボックスを閉じます。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 スキーマ オプションは、1 つまたは複数のオプションについて、 [| (ビット演算 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) を実行した結果を 16 進数値で指定します。 詳細については、「 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 」および「 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)」を参照してください。  
  
> [!NOTE]  
>  ビットごとの演算を実行する際は、あらかじめ、スキーマ オプションの値を **binary** から **int** に変換しておく必要があります。 詳細については、「[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを定義するときにスキーマ オプションを指定するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前、 ** \@ アーティクルのアーティクルの名前、** ** \@ source_object**にパブリッシュするデータベースオブジェクト、 ** \@ 種類**としてデータベースオブジェクトの種類、| を指定します。 [(ビットごとの OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql)** \@ schema_option**の1つ以上のスキーマオプションの結果。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a>マージ パブリケーションのアーティクルを定義するときにスキーマ オプションを指定するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前、**アーティクルのアーティクル名、 \@ ** ** \@ source_object**にパブリッシュするデータベースオブジェクト、および | を指定します。 [(ビットごとの OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql)** \@ schema_option**の1つ以上のスキーマオプションの結果。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションの既存のアーティクルに設定されているスキーマ オプションを変更するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前と、アーティクルのアーティクルの名前を指定し** \@ ます。** 結果セットの **schema_option** 列の値を確認してください。  
  
2.  手順 1 の値、および必要なスキーマ オプションの値を使って [& (ビット演算 AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 演算を実行し、対象のオプションが設定されているかどうかを確認します。  
  
    -   実行結果が **0**の場合、オプションは設定されていません。  
  
    -   実行結果がオプションの値の場合、そのオプションは既に設定されています。  
  
3.  オプションが設定されていなかった場合は、手順 1. の値と、必要なスキーマ オプション値を使って [| (ビット演算 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 演算を実行します。  
  
4.  パブリッシャーのパブリケーション データベースで [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前 **、アーティクルの \@ **アーティクル名、 ** \@ プロパティ**に**schema_option**の値、および手順 3. の16進数の結果を [ ** \@ 値**] に指定します。  
  
5.  スナップショット エージェントを実行して、新しいスナップショットを生成します。 詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a>マージ パブリケーションの既存のアーティクルのスキーマ オプションを変更するには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前と、アーティクルのアーティクルの名前を指定し** \@ ます。** 結果セットの **schema_option** 列の値を確認してください。  
  
2.  手順 1 の値、および必要なスキーマ オプションの値を使って [& (ビット演算 AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 演算を実行し、対象のオプションが設定されているかどうかを確認します。  
  
    -   実行結果が **0**の場合、オプションは設定されていません。  
  
    -   実行結果がオプションの値の場合、そのオプションは既に設定されています。  
  
3.  オプションが設定されていなかった場合は、手順 1. の値と、必要なスキーマ オプション値を使って [| (ビット演算 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 演算を実行します。  
  
4.  パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)を実行します。 ** \@ パブリケーション**のアーティクルが属しているパブリケーションの名前 **、アーティクルの \@ **アーティクル名、 ** \@ プロパティ**に**schema_option**の値、および手順 3. の16進数の結果を [ ** \@ 値**] に指定します。  
  
5.  スナップショット エージェントを実行して、新しいスナップショットを生成します。 詳しくは、「 [初期スナップショットの作成および適用](../create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md)   
 [Article Options for Transactional Replication](../transactional/article-options-for-transactional-replication.md)  
  
  
