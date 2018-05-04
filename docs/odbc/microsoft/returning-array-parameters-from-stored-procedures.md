---
title: 配列パラメーターを返すストアド プロシージャ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f07c82501822c4c2afebe54390baffc6072e799
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="returning-array-parameters-from-stored-procedures"></a>ストアド プロシージャから返される配列パラメーター
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 7.3、PL/SQL プログラムから除く PL/SQL レコードの種類にアクセスする方法はありません。 パッケージ化されたプロシージャまたは関数の仮引数の PL/SQL レコードの種類として定義されている場合、その仮引数をパラメーターとしてバインドすることはできません。 Microsoft ODBC Driver for Oracle の PL/SQL テーブル型を使用して、適切なエスケープ シーケンスを含むプロシージャから配列パラメーターを呼び出します。  
  
 プロシージャを呼び出すには、次の構文を使用します。  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  \<最大レコード要求 > パラメーターが、結果セットに存在する行の数以上にする必要があります。 それ以外の場合、Oracle では、ドライバーによって、ユーザーに渡されるエラーを返します。  
>   
>  PL/SQL レコードは、配列パラメーターとして使用できません。 各配列パラメーターには、データベース テーブルの 1 つだけの列を表すことができます。  
  
 次の例では、それぞれ異なる結果セットを返す 2 つの手順を含むパッケージを定義し、パッケージから結果セットを返す 2 つの方法を提供します。  
  
## <a name="package-definition"></a>パッケージの定義:  
  
```  
CREATE OR REPLACE PACKAGE SimplePackage AS  
  
TYPE t_id is TABLE of  NUMBER(5)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Course is TABLE of VARCHAR2(10)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Dept is TABLE of VARCHAR2(5)  
    INDEX BY BINARY_INTEGER;  
  
PROCEDURE proc1  
   (  
   o_id             OUT    t_id,  
   ao_course       OUT    t_Course,  
   ao_dept         OUT    t_Dept  
   );  
  
TYPE t_pk1Type1 IS TABLE OF VARCHAR2(100) INDEX BY BINARY_INTEGER;  
TYPE t_pk1Type2 IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   );  
  
END SimplePackage;  
  
CREATE OR REPLACE PACKAGE BODY SimplePackage AS  
    PROCEDURE  proc1 ( o_id OUT t_id,  
    ao_course OUT t_Course, ao_dept OUT t_Dept   ) AS  
    BEGIN  
          o_id(1):= 200;  
          ao_course(1) :=  'M101';  
          ao_dept(1) :=  'EEE' ;  
  
          o_id(2) := 201;  
          ao_course(2) :=  'PHY320';  
          ao_dept(2) :=  'ECE' ;  
  
     END proc1;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   )  
AS  
   i   NUMBER;  
BEGIN  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg2(i) := 'Row Number ' || to_char(i);  
   END LOOP;  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg3(i) := i;  
   END LOOP;  
END proc2;  
END SimplePackage;  
```  
  
#### <a name="to-invoke-procedure-proc1"></a>手順 1 のプロシージャを呼び出す  
  
1.  1 つの結果セット内のすべての列が返されます。  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  単一の結果セットとして各列を返します。  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     これには、列ごとに 1 つ、3 つの結果セットが返されます。  
  
#### <a name="to-invoke-procedure-proc2"></a>手順 2 のプロシージャを呼び出す  
  
1.  1 つの結果セット内のすべての列が返されます。  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  単一の結果セットとして各列を返します。  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 すべての結果セットを使用して、アプリケーションがフェッチことを確認してください、 [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) API です。 詳細についてを参照してください、 *ODBC プログラマ リファレンス*です。  
  
> [!NOTE]  
>  Oracle version 2.0 の ODBC ドライバーでは、結果セットを返す PL/SQL 配列を返す Oracle 関数を使用できません。
