    # **CONTRATO DE PRESTAÇÃO DE SERVIÇOS**

    **Quadro Resumo**

    |    **I.    CONTRATANTE** |
    |:--- |
            % for i in contratante:
            I.1.        **${ i.name.first }**, pessoa jurídica de direito privado, inscrita no CNPJ/MF sob o nº ${ i.cnpj }, com sede no endereço ${ title_case(i.address.street) }, nº ${ i.address.street_number }, 
            % if i.address.unit: 
            ${ title_case(i.address.unit) }, 
            % endif
            ${ title_case(i.address.neighborhood) }, ${ title_case(i.address.city) }/${ i.address.state }, CEP ${ i.address.zip }, neste ato devidamente representada por seu representante legal.
            % endfor 
            % if contratante_inserirDadosGestor: 
            Dados de contato do gestor do Contrato:
            Nome: ${ contratante_nome_gestor }
            % if contratante_email_gestor:
            E-mail: ${ contratante_email_gestor }
            % endif
            % if contratante_telefone_gestor:
            Telefone: ${ contratante_telefone_gestor }
            % endif
            % endif
    |    **II.    CONTRATADA** |
    |:--- |
            % for i in contratada:
            **II.1.        ${ i.name.first }**, 
            % if i.tipo_pessoa == 'Jurídica':
            pessoa jurídica de direito privado, inscrita no CNPJ/MF sob o nº ${ i.cnpj }, com sede no endereço ${ title_case(i.address.street) }, nº ${ i.address.street_number }, 
            % if i.address.unit:
            ${ title_case(i.address.unit) }, 
            % endif
            ${ title_case(i.address.neighborhood) }, ${ title_case(i.address.city) }/${ i.address.state }, CEP ${ i.address.zip }, neste ato devidamente representada por seu representante legal.
            % else:
            ${ i.nacionalidade }, ${ i.estado_civil }, ${ i.profissao }, inscrito(a) no CPF/MF sob o nº ${ i.cpf } e portador(a) da Carteira de Identidade (RG) nº ${ i.rg }, residente e domiciliado(a) no endereço ${ title_case(i.address.street) }, nº ${ i.address.street_number }, 
            % if i.address.unit:
            ${  title_case(i.address.unit) }, 
            % endif
            ${ title_case(i.address. neighborhood) }, ${ title_case(i.address.city) }/${ i.address.state }, CEP ${ i.address.zip }.
            % endif
            % endfor
            % if contratada_inserirDadosGestor:
            Dados de contato do gestor do Contrato:
            Nome: ${ contratada_nome_gestor }
            % if contratada_email_gestor:
            E-mail: ${ contratada_email_gestor }
            % endif
            % if contratada_telefone_gestor:
            Telefone: ${ contratada_telefone_gestor }
            % endif
            % endif
    |    **III.    OBJETO** |
    |:--- |
            **III.1.**    O presente Contrato tem como objeto a prestação dos serviços de ${ objeto }, pela **CONTRATADA** à **CONTRATANTE** ('Serviços').
            **III.2.**    A 
            % if contratadaForneceEquipamentos:
            **CONTRATADA** ficará responsável por qualquer material, ferramenta, utensílio e equipamento necessário, direta ou indiretamente, para a prestação dos Serviços, inclusive pela respectiva manutenção, uma vez que referidas despesas já estão incluídas no Preço.
            % else:
            **CONTRATANTE** ficará responsável pelo fornecimento dos materiais e equipamentos diretamente necessários para a prestação dos Serviços, ficando claro desde já que referidos equipamentos deverão ser restituídos à **CONTRATANTE** ao final deste Contrato, caso não tenham sido consumidos durante a prestação dos Serviços.
            % endif
            % if temAnexo:
            **III.3.**    As demais especificações referentes aos Serviços ora contratados estão previstas no Anexo ao presente Contrato.
            % endif
    |    **IV.    PREÇO E FORMA DE PAGAMENTO** |
    |:--- |
            **IV.1.**        Pela execução dos Serviços objeto deste Contrato, a **CONTRATANTE** pagará à **CONTRATADA** o valor ${ tipoParcela } de R$ ${ "%.2f"|format(valorContrato) | replace(".",",") } (${ valorContratoExtenso }) ("Preço").
            **IV.2.**        O pagamento do Preço será realizado 
            % if tipoParcela == 'mensal':
            mensalmente
            % else:
            % if formaPagamento == 'a_vista': 
            à vista na data de entrega dos Serviços
            % else:
            % if nrParcelas > 0:
            em ${ nrParcelas }(${nrParcelasExtenso }) parcelas
            % endif
            % if temAnexo:
            , conforme cronograma de pagamento descrito no Anexo
            % endif
            % endif
            % endif
            , mediante 
            % if tipoPagamento == 'conta corrente':
            depósito em conta corrente: 
            banco: ${ banco }, agência: ${ agencia }, conta corrente: ${ contaCorrente }, 
            % if tipo_pessoa_cc == 'Física':
            CPF ${ cpf_cc }
            % else:
            CNPJ ${ cnpj_cc }
            % endif
            % else:
            pagamento de boleto bancário
            % endif.
            **IV.3.**        As despesas de locomoção, estadia e alimentação incorridas pelas pessoas que prestarão os Serviços serão de responsabilidade da 
            % if pgtoDespesasExtras == 'Contratada':
            **CONTRATADA**, uma vez que referidas despesas já estão incluídas no Preço
            % else:
            **CONTRATANTE**, desde que sejam previamente aprovadas por escrito pela **CONTRATANTE** 
            % endif.
    |    **V.    PRAZO** |
    |:--- |
            **V.1.**        O presente Contrato irá vigorar de ${ prazoInicio } até ${ prazoFim }. |
    |    **VI.    LOCAL DA PRESTAÇÃO DOS SERVIÇOS** |
    |:--- |
            **VI.1.**        A execução dos Serviços ocorrerá nas dependências da ${ **localExecucaoServicos ** }
    % if localExecucaoServicos == 'Contratante':
    , na ${ logradouroExecucaoServicos }, das ${ horaInicioExecucaoServicos }h. às ${ horaFimExecucaoServicos }h., em dias ${ diasTrabalho.true_values() }.
    % endif
            **VI.2.**        Caso haja necessidade de atendimento corretivo ou emergencial fora do horário e dos dias previstos acima, as Partes deverão acordar previamente por escrito as condições para a realização de tais Serviços emergenciais.
    % if temExclusividade:
    |    **VII.    EXCLUSIVIDADE** |
    |:--- |
            **VII.1.**        O presente Contrato prevê exclusividade por parte da **CONTRATADA** no que se refere ao segmento de atuação da **CONTRATANTE** nas atividades que compõem o escopo deste instrumento, não podendo a **CONTRATADA** , seja diretamente, seja por intermédio de pessoa interposta, prestar os Serviços objeto deste Contrato a qualquer outra pessoa, física ou jurídica concorrente da **CONTRATANTE** , enquanto perdurar este Contrato.
    % endif
    % if temAnexo:
    |    **VIII.    ANEXOS** |
    |:--- |
            **VIII.1.**        São partes integrantes deste instrumento os seguintes Anexos:
    % for item in anexos:
    - Anexo: ${ item.filename }
    % endfor
    % endif

    CONTRATO DE PRESTAÇÃO DE SERVIÇOS

    Pelo presente instrumento particular, as Partes acima qualificadas no Quadro Resumo resolvem celebrar o presente Contrato de Prestação de Serviços ("Contrato"), que tem por finalidade estabelecer os direitos e obrigações das Partes na execução contratual, de acordo com a legislação vigente, mediante as cláusulas e condições adiante estabelecidas.

    **1.    OBJETO**

        1.1.    O presente Contrato tem por objeto a prestação, por parte da **CONTRATADA** à **CONTRATANTE** , dos Serviços especificados no item III do Quadro Resumo acima, e atividades correlacionadas.  Para tanto, a **CONTRATADA** obriga-se a fornecer mão de obra especializada e devidamente habilitada.

          1.1.1.    As demais especificações referentes aos Serviços ora contratados estão previstas no(s) anexo(s) ao presente Contrato, conforme aplicável.

        1.2.    A prestação dos Serviços será realizada com equipe própria da **CONTRATADA** , alocada nas dependências da **CONTRATANTE**.

    **2.    VIGÊNCIA**

        2.1.    O Contrato vigorará pelo prazo estabelecido no item V do Quadro Resumo.

        2.2.    As Partes poderão acordar a prorrogação do prazo estabelecido acima mediante a celebração de termo aditivo ao presente Contrato.

    **3.    LOCAL DA PRESTAÇÃO DOS SERVIÇOS**

        3.1.    A execução dos Serviços ocorrerá no local previsto no item VI do Quadro Resumo.

        3.2.    Caso haja necessidade de atendimento corretivo ou emergencial fora do horário e dos dias previstos acima, as Partes deverão acordar previamente por escrito as condições para a realização de tais Serviços emergenciais.

    **4.    PREÇO**

        4.1.    A **CONTRATANTE** pagará à **CONTRATADA** , pela prestação dos Serviços ora contratados, o valor previsto no item IV do Quadro Resumo (" **Preço**").

          4.1.1.    Exceto conforme previsto no item IV do Quadro Resumo, o Preço é a única remuneração da **CONTRATADA** pela execução dos Serviços, incluindo a totalidade das despesas, ônus, custos de qualquer espécie, tributos, seguros, mobilização, permanência e desmobilização de equipamentos e mão-de-obra e tributos incidentes.

          4.1.2.    Os tributos que forem devidos em decorrência direta ou indireta deste Contrato, ou de sua execução, constituem ônus econômico da **CONTRATADA** , que desde já autoriza a **CONTRATANTE** a proceder à respectiva retenção, quando a legislação assim exigir, cabendo os respectivos recolhimentos ao sujeito passivo, seja como contribuinte ou responsável, conforme definido na lei tributária.

        % if reajusteAnual:
        4.2.    O Preço poderá ser reajustado anualmente, aplicando-se o 
          % if tipoReajuste == 'IGP-M':
          Índice Geral de Preços do Mercado – IGP-M
          % else:
          Índice Nacional de Preços ao Consumidor Amplo - IPCA
          % endif.
        Na hipótese de extinção do referido índice, será utilizado índice oficial que vier a substituí-lo.
        % endif

    **5.    CONDIÇÕES DE PAGAMENTO**

        5.1.    O Preço será pago pela **CONTRATANTE** à **CONTRATADA** , de acordo com as especificidades previstas no item IV do Quadro Resumo.

        5.2.    A emissão da respectiva nota fiscal pela **CONTRATADA** em valores diversos do pactuado nesteContratodependerá de prévia autorização da **CONTRATANTE** por escrito, mediante a respectiva solicitação pela **CONTRATADA**.

        5.3.    O pagamento do Preço será realizado mediante o envio pela **CONTRATADA** de nota fiscal para pagamento, com antecedência mínima de 30 (trinta) dias do vencimento.

          5.3.1.    A nota fiscal/fatura apresentada após o prazo determinado acima terá seu vencimento automaticamente prorrogado na mesma quantidade de dias do atraso e sem quaisquer acréscimos adicionais e sem configuração de mora da **CONTRATANTE**.

          5.3.2.    Na hipótese de incorreção da nota fiscal/fatura, ela será devolvida pela **CONTRATANTE** à **CONTRATADA** para retificação, devendo ser restabelecido, integralmente, o prazo de pagamento.

          5.3.3.    Caso o vencimento da nota fiscal/fatura incida em dia não útil, será prorrogado o pagamento para o 1º (primeiro) dia útil bancário subsequente.

          5.3.4.    O atraso de quaisquer parcelas do Preço acarretará a incidência de multa fixa de 1% (um por cento) ao mês sobre o valor em atraso e juros de mora calculados à taxa de 1% (um por cento) ao mês, incidentes _pro rata temporis_, a partir do primeiro dia subsequente ao término do prazo estabelecido.

          5.3.5.    A **CONTRATANTE** não realizará nenhum pagamento, de qualquer natureza, a qualquer empregado, funcionário, representante e/ou contratado da **CONTRATADA** , que venha a prestar os Serviços objeto deste Contrato, visto que não há qualquer tipo de relação obrigacional e/ou empregatícia entre a **CONTRATANTE** e os funcionários empregados, representantes e/ou contratado da **CONTRATADA**.

    **6.    MÃO DE OBRA**

        6.1.    A **CONTRATADA** responsabiliza-se a fazer cumprir, por seu pessoal, as normas internas adotadas pela **CONTRATANTE** pertinentes à segurança geral, higiene, medicina e segurança do trabalho, proteção ao patrimônio e prevenção de incêndios ou qualquer outra instrução prescrita pela **CONTRATANTE**.

        6.2.    Toda e qualquer pessoa alocada pela **CONTRATADA** na prestação dos Serviços terá subordinação direta a um dos representantes da **CONTRATADA** , não havendo entre tais pessoas e a **CONTRATANTE** qualquer vínculo ou relação empregatícia.

        6.3.    A mão-de-obra utilizada pela **CONTRATADA** nos estabelecimentos da **CONTRATANTE** deverá ser devidamente treinada e especializada, apresentar-se devidamente uniformizada, obedecendo aos requisitos legais e aos princípios éticos de respeito, organização e postura perante o pessoal da **CONTRATANTE** , bem como perante terceiros com os quais venha a se relacionar no desempenho de suas funções, sendo facultado à **CONTRATANTE** , a seu exclusivo critério, o direito de solicitar a substituição de qualquer funcionário, preposto ou subcontratado da **CONTRATADA** , a qualquer tempo, solicitação essa que deverá ser atendida de forma planejada e acordada entre as partes.

        6.4.    A **CONTRATADA** deverá manter, sempre que necessário, um funcionário com poderes de decisão que lhe permita responder, entre outras, mas sem se limitar a, pelas seguintes atividades:

        a)    entender-se com o representante da **CONTRATANTE** sobre o andamento e qualidade dos Serviços;
        b)    controlar a frequência e horário de seus funcionários alocados na **CONTRATANTE** para a prestação dos Serviços, instruindo-os sobre a correta execução dos Serviços;
        c)    instruir seus funcionários alocados na **CONTRATANTE** para a prestação dos Serviços, periodicamente, quanto ao cumprimento das normas internas de conduta e segurança da **CONTRATANTE** ;
        d)    manter, diariamente, a equipe de trabalho completa, suprindo eventual ausência em até 04 (quatro) horas contadas da solicitação da **CONTRATANTE** ;
        e)    manter registros atualizados de todas as atividades desenvolvidas, material utilizado e eventos extraordinários ocorridos, sendo certo que tais registros deverão ser conservados nas dependências da **CONTRATANTE** sob a sua guarda e poderão ser verificados, pela **CONTRATANTE** ou por seu representante, sempre que julgarem conveniente;

        6.5.    A **CONTRATADA** será a única e exclusiva responsável por todas as obrigações de ordem civil, trabalhista previdenciária, securitária e qualquer outra relativa a toda e qualquer pessoa por ela incumbida para a prestação dos Serviços, inclusive sócios, prepostos e mandatários, não cabendo à **CONTRATANTE** qualquer responsabilidade perante autoridades ou terceiros, em decorrência de autuações ou prejuízos que possam advir, à **CONTRATADA** e/ou à **CONTRATANTE** , do não-cumprimento do disposto nesta cláusula.

        6.6.    É vedado à **CONTRATADA** , bem como a seus empregados, interferir nas atividades de rotina da **CONTRATANTE** , exceto quando necessário à execução dos Serviços, o que deverá obrigatoriamente ser informado prévia e expressamente à **CONTRATANTE** , com no mínimo 72 (setenta e duas) horas de antecedência.

        6.7.    A **CONTRATANTE** fornecerá todo o apoio que se fizer necessário para a plena realização e execução dos Serviços ora contratados.

        6.8.    A **CONTRATADA** deverá enviar à **CONTRATANTE** os seguintes documentos, relativos aos seus empregados que prestarão os Serviços:

              a)     no início de vigência do Contrato (e sempre que tais documentos sofrerem alterações após tal data):

                i)     contrato/estatuto Social da **CONTRATADA** com registro na Junta Comercial e última alteração contratual, incluindo ato de eleição da atual administração;
                ii)     cartão CNPJ;
                iii)    declaração firmada pelo contador e administrador da **CONTRATADA** atestando que esta possui escrituração própria e regular;
                iv)   caso a **CONTRATADA** seja registrada no Sistema de Apuração de Tributos baseado no SIMPLES, apresentar o referido Termo;
                v)    cópia da Carteira de Trabalho e Previdência Social e do Contrato de Trabalho de cada um dos funcionários alocados na prestação dos Serviços;
                vi)   cópia da Ficha de Entrega de EPI's.

              b)    mensalmente:

                i)    cópia da folha de pagamento;
                ii)   cópia autenticada da GFIP – Guia de Recolhimento do FGTS e Informações à Previdência, com o correspondente comprovante de recolhimento de FGTS e INSS;
                iii)    cópia dos termos de rescisão de contratos ocorridos no mês, com comprovante de pagamento das verbas rescisórias, cópia da guia de FGTS, cópia do Perfil Profissiográfico Profissional e exame demissional;
                iv)   cópia dos comprovantes de pagamento dos salários e demais verbas e benefícios;
                v)    cópia da Ficha de Registro dos Empregados;
                vi)   cópia do Cartão de Ponto;
                vii)    cópia do Atestado de Saúde Ocupacional - ASO (antes do início da prestação de serviços).

              c)    anualmente:

                i)    cópia do Certificado de Regularidade do FGTS;
                ii)   cópia da Certidão Negativa de INSS;
                iii)    Certidão de Débitos relativos a Créditos Tributários Federais e à Dívida Ativa da União;
                iv)   Certidão Negativa de Débitos Municipais com a Secretaria onde está localizada a sede da **CONTRATADA** ;
                v)    Cópia dos recibos de férias.

              d)    sempre que solicitado, quaisquer outros documentos que a **CONTRATANTE** julgar necessário.

        6.9.    A **CONTRATADA** obriga-se ainda a:

            a)    não empregar menor de 18 (dezoito) anos, inclusive menor aprendiz, em locais prejudiciais à sua formação, ao seu desenvolvimento físico, psíquico, moral e social, bem como em locais e serviços perigosos ou insalubres, em horários que não permitam a frequência à escola, e ainda, em horárionoturno, considerando este o período compreendido entre as 22h e 6h;
            b)    não utilizar práticas de discriminação negativas, e limitativas ao acesso na relação de emprego ou à sua manutenção, tais como, mas não se limitando a, por motivos de: sexo, origem, raça, cor, condição física, religião, estado civil, idade, situação familiar ou estado gravídico;
            c)    bservar o limite legal da jornada semanal de trabalho de 8 (oito) horas diárias e 44 (quarenta e quatro) horas semanais, facultando-se a prorrogação de horário no máximo em 02 (duas) horas, assegurando o acréscimo de 50% (cinquenta por cento) sobre a hora normal, ressalvada taxa superior prevista em norma coletiva, nos termos do art. 59 da CLT;
            d)    manter um rígido controle sobre todos os trabalhadores que prestarem os Serviços e, inclusive, manter a **CONTRATANTE** informada neste sentido, cabendo, portanto, à **CONTRATADA**:

              i)    Fornecer mensalmente à **CONTRATANTE** trabalhistas, previdenciários e/ou quaisquer outros relacionados ao vínculo empregatício existente entre a **CONTRATADA** e seus empregados que trabalhem para a execução dos Serviços;
              ii)   sempre que qualquer dos empregados mencionados no inciso &quot;i&quot; acima deixar de prestar os Serviços, avisar de imediato e por escrito à **CONTRATANTE** ;
              iii)    em se tratando de novos trabalhadores que prestarão os Serviços (substituição e/ou inclusão), obriga-se a **CONTRATADA** a atender o previsto no inciso &quot;i&quot; acima, no primeiro dia em que essa nova pessoa ingressar nas dependências da **CONTRATANTE** ;
              iv)   quando os Serviços estiverem em andamento, entregar à **CONTRATANTE** no prazo de 24 (vinte e quatro) horas a relação de todos os trabalhadores que estejam prestando os Serviços, a contar da data/hora em que a **CONTRATANTE** lhe entregar solicitação neste sentido.

            e)cumprir todas as normas regulamentadoras editadas pelo Ministério do Trabalho aplicadas à espécie, bem como as normas de saúde, de meio ambiente e de segurança interna da **CONTRATANTE** , devendo os trabalhadores que executarão os Serviços usarem todos os EPI's (equipamentos de proteção individual), necessários para a realização dos Serviços ora contratados, conforme aplicável;
            f)    fazer com que os trabalhadores que irão executar os Serviços se identifiquem na Portaria da **CONTRATANTE** , inclusive durante a execução destes, por meio do respectivo documento de identidade e/ou crachás, os quais deverão obedecer rigorosamente a todas as normas ou procedimentos internos da **CONTRATANTE** ;
            g)    afastar imediatamente das dependências da **CONTRATANTE** qualquer preposto ou empregado seu cuja permanência ou conduta seja considerada inconveniente ou irregular a exclusivo critério da **CONTRATANTE** ;
            h)    responsabilizar-se pelas despesas e/ou fornecimento de transporte e/ou alimentação em relação a todos os trabalhadores que executarão os Serviços, ficando a **CONTRATANTE** totalmente isenta de quaisquer responsabilidades e/ou ônus neste sentido.

        6.10.   Considerando que irregularidades da **CONTRATADA** , em descumprimento à legislação vigente, inclusive no que se refere às obrigações trabalhistas, previdenciárias, fundiárias, tributárias e ambientais, podem expor indevidamente a **CONTRATANTE** a riscos e contingências relevantes, em decorrência de solidariedade e/ou obrigações subsidiárias, as partes convencionam e declaram que as obrigações estipuladas nas Cláusulas 6.8 e 6.9 acima são obrigações principais do presente Contrato e, juntamente com a prestação dos Serviços ora contratados, constituem causa para o recebimento da remuneração devida à **CONTRATADA**.

          6.10.1.   Caso a **CONTRATADA** deixe de comprovar a sua regularidade, nos termos e prazo previstos nas Cláusulas 6.8 e 6.9 acima, a **CONTRATANTE** poderá reter os pagamentos devidos à **CONTRATADA** , observando-se, nesse sentido, o seguinte:

            a)    a retenção aqui prevista não ensejará mora, nos termos do artigo 476 do Código Civil brasileiro;
            b)    em ocorrendo o previsto nesta Cláusula 6.10.1, ficará caracterizado o descumprimento contratual por parte da **CONTRATADA** e a justa causa para rescisão do presente Contrato. Assim, a **CONTRATANTE** poderá, a seu exclusivo critério, dar por rescindido de imediato este Contrato, para todos os fins e efeitos de direito, arcando a **CONTRATADA** com todas as consequências respectivas;
            c)    em sendo rescindido ou não o presente Contrato, o(s) valor(es) retido(s) somente será(ao) pago(s) efetivamente à **CONTRATADA** quando esta entregar à **CONTRATANTE** todos os documentos que comprovam a sua regularidade, em atendimento à solicitação da **CONTRATANTE** conforme previsto nas Cláusulas 6.8 e 6.9 acima, sem prejuízo do disposto no item &quot;d&quot; abaixo;
            d)    (s) valor(es) retido(s) poderá(ão) ser utilizado(s) pela **CONTRATANTE** para fazer depósitos, na hipótese dela ter contra si quaisquer ações judiciais relativas aos Serviços ora contratados ou para sanar eventuais irregularidades da **CONTRATADA** ; e
            e)    na hipótese da **CONTRATANTE** ter que ajuizar medidas judiciais para sustação de protestos de títulos emitidos pela **CONTRATADA** e não pagos no vencimento em virtude do exercício da retenção pela **CONTRATANTE** , conforme previsto acima, obriga-se a **CONTRATADA** ressarcir, de imediato, todas as despesas, custas e honorários advocatícios despendidos pela **CONTRATANTE** para defesa de seus direitos, sem prejuízo do disposto no item "b" supra.

        6.11.   Não se estabelece, por força do presente Contrato, nenhum vínculo empregatício entre a **CONTRATANTE** e os empregados, prepostos, terceirizados e/ou subcontratados ou terceiros da **CONTRATADA** , cabendo a esta última, todas as responsabilidades trabalhistas, securitárias, previdenciárias e fiscais, inclusive aquelas oriundas de modificações na legislação em vigor, concernente aos seus empregados e/ou subcontratados envolvidos na execução do presente Contrato, vinculados direta ou indiretamente à **CONTRATADA** , devendo a **CONTRATADA** reembolsar à **CONTRATANTE** , no prazo de 03 (três) dias a contar da solicitação, quaisquer despesas decorrentes de reclamações trabalhistas, ações judiciais diversas e/ou processos administrativos, de qualquer natureza, inclusive os relativos a acidente de trabalho, promovidos pelas pessoas descritas nesta cláusula, sendo que todos os valores serão corrigidos pelo IPCA, desde a data do desembolso pela **CONTRATANTE** até a data do pagamento pela **CONTRATADA**.

    **7.    OBRIGAÇÕES DA CONTRATADA**

        7.1.    A **CONTRATADA** deverá executar os Serviços ora contratados de acordo com a melhor técnica e diligência, e deverá observar as solicitações dos colaboradores da **CONTRATANTE** , procedendo às correções que forem necessárias conforme solicitado pela **CONTRATANTE**.

        7.1.1.    A **CONTRATADA** , por sua exclusiva conta e risco, obriga-se a mandar refazer o s Serviços objeto deste Contrato que tenham sido executados com defeitos de qualquer espécie.

        7.2.    É vedado à **CONTRATADA** assumir quaisquer despesas em nome da **CONTRATANTE** que não tenham sido previamente autorizadas por escrito pela **CONTRATANTE**. É também vedado à **CONTRATADA** dar ou oferecer qualquer tipo de pagamento ou benefício para qualquer terceiro, pessoa física ou jurídica, incluindo órgãos governamentais, com a intenção de influenciá-los em qualquer ato ou concorrência, relacionado de alguma forma com as atividades deste Contrato, como também é vedado oferecer gratificações ou similares a funcionários e parentes de funcionários da **CONTRATANTE**.

        7.3.    A **CONTRATADA** executará os Serviços por meio de trabalhadores contratados sob o regime da CLT (Consolidação das Leis do Trabalho), com regular registro em carteira e devidamente treinados e capacitados para desenvolver satisfatoriamente as atividades ora contratadas, sendo expressamente proibida a subcontratação dos Serviços.

        7.4.    Cabe à **CONTRATADA** cumprir todas as exigências legais e fiscais decorrentes da execução do presente Contrato, quer no âmbito federal, estadual e/ou municipal, de forma que nenhuma reclamação seja dirigida à **CONTRATANTE** em virtude da inobservância pela **CONTRATADA** de suas obrigações.

        7.4.1.    A **CONTRATADA** obriga-se a cumprir todas as leis e disposições de caráter trabalhista, acidentário e previdenciário, com referência a todos os profissionais por ela contratados para a execução dos Serviços, efetuando todos os descontos e recolhimentos, a quem de direito, de todos e quaisquer tributos e contribuições que por lei ou convenções forem devidos. Em sendo ajuizadas ações judiciais contra a **CONTRATANTE** envolvendo funcionários alocados na **CONTRATANTE** pela **CONTRATADA** para a prestação dos Serviços em função deste Contrato, ou mesmo em havendo notificações do Ministério do Trabalho ou procedimentos perante o Ministério Público do Trabalho neste sentido, obriga-se a **CONTRATADA** a intervir nos processos reivindicando a condição de demandada e requerendo a exclusão da **CONTRATANTE** da lide em questão. Na hipótese de não ser admitida a intervenção da **CONTRATADA** e/ou a exclusão da **CONTRATANTE** nos processos, ainda assim permanecerá a **CONTRATADA** como única e exclusiva responsável por referido processo, estando sujeita às previsões contratuais aqui estabelecidas, bem como à legislação pertinente.

        7.4.2.    A **CONTRATADA** obriga-se, da mesma forma, a cumprir todas as normas de saúde, meio ambiente e segurança nos termos da legislação vigente.

        7.5.    A **CONTRATADA** deverá manter registros completos, apresentando-os à **CONTRATANTE** , sempre que solicitado, de todos os documentos e informações resultantes deste Contrato, observando sempre a legislação aplicável até o decurso de todos os prazos de prescrição ou decadência referentes a direitos que possam ser reclamados da **CONTRATANTE** e/ou da **CONTRATADA** por terceiros ou pelas autoridades competentes.

        7.5.1.    As Partes concordam que, para os fins deste Contrato, o prazo para guarda de documentos é de: (i) 7 (sete) anos após o encerramento do ano fiscal a que os registros se referem, para registros fiscais e de contribuições previdenciários; e (ii) 5 (cinco) anos para registros de natureza trabalhista, a contar da data de desligamento de cada profissional alocado na presente prestação dos Serviços.

        7.6.    Caso a **CONTRATANTE** seja acionada na esfera judicial por trabalhador destacado pela **CONTRATADA** para a prestação dos Serviços objeto do presente Contrato, poderá a **CONTRATANTE** , após o recebimento da respetiva notificação judicial, reter dos pagamentos a serem realizados à **CONTRATADA** por força deste instrumento a importância correspondente aos valores efetivamente discutidos nos autos do processo judicial em questão, como forma de se garantir contra eventual perda. A retenção aqui prevista não ensejará mora, e tampouco descumprimento contratual por parte da **CONTRATANTE**.

        7.7.    Além de outras obrigações previstas neste Contrato, obriga-se a **CONTRATADA** a:

              a)    observar todas as leis, regulamentos e requisitos legais emanados de quaisquer autoridades governamentais e/ou entidades com poderes normativos. Na hipótese de violação, ou não cumprimento, pela **CONTRATADA** , de quaisquer leis, regulamentos, exigências ou requisitos legais, a **CONTRATADA** arcará exclusivamente com as consequências de tais descumprimentos, isentando a **CONTRATANTE** de eventuais reclamações, perdas e/ou prejuízos, litigiosos ou não, resultantes de tais atos.
              b)    responder pelo pagamento de todos os tributos federais, estaduais e municipais relacionados direta e/ou indiretamente com o objeto deste Contrato, além dos incidentes sobre a remuneração recebida da **CONTRATANTE**.
              c)    responder pela inobservância ou infração de qualquer cláusula ou condição deste Contrato.
              d)    prestar, sempre que solicitado, à **CONTRATANTE** ou a quem ela indicar, por escrito, esclarecimentos que sejam considerados necessários à perfeita compreensão dos Serviços executados.
              e)    utilizar mão-de-obra que melhor se adaptar às características dos Serviços ora contratados.
              f)    executar os Serviços utilizando-se do melhor critério e técnica mais recomendável, observando quaisquer indicações e recomendações feitas nesse sentido pela **CONTRATANTE**.
              g)    informar imediatamente à **CONTRATANTE** sobre qualquer ocorrência ou irregularidade que venha a afetar a perfeição da execução e/ou do andamento dos Serviços.
              h)    sempre que solicitado pela **CONTRATANTE** , prestar informações, por escrito, sobre o andamento dos Serviços, inclusive sobre ocorrências e irregularidades.
              i)    assegurar a integridade física do pessoal que, sob a sua responsabilidade direta ou indireta, esteja encarregado dos Serviços, do funcionário da **CONTRATANTE** e/ou de terceiros que estejam alocados nas instalações onde serão prestados os Serviços, conforme aplicável, bem como assegurar a integridade do patrimônio da **CONTRATANTE** e/ou de terceiros a que tiver acesso em função do presente Contrato, responsabilizando-se civil, penal e/ou administrativamente pelos atos e/ou fatos ilícitos, danos pessoais a/ou patrimoniais que seu pessoal vier a causar, dolosa ou culposamente, à **CONTRATANTE** e/ou a terceiros, arcando a **CONTRATADA** com todos os custos decorrentes de tais atos.
              j)    providenciar e manter vigente, às suas expensas e durante toda a vigência do presente Contrato, seguros de acidentes de trabalho relativamente ao pessoal por ela encarregado de prestar os Serviços, bem como todos os demais seguros necessários à cobertura de eventuais danos ou prejuízos decorrentes, vinculados ou conexos a prestação dos Serviços a/ou a atos imputáveis a sua equipe de trabalho.
              k)    remover, ao término do presente Contrato, todos os materiais, equipamentos, ferramentas e utensílios de sua propriedade, utilizados na execução dos Serviços, conforme aplicável;
              l)    exibir e renovar, no curso do Contrato, sempre que solicitadas, as licenças e autorizações exigidas para o exercício das suas atividades relacionadas aos Serviços ora contratados.
              % if temOutraObrigacao:
                % for item in obrigacao:
                  % set contador = 13
              m)    ${ item.name.text }{% endfor %}{% endif %}

    **8.    OBRIGAÇÕES DA CONTRATANTE**

        8.1.    São obrigações da **CONTRATANTE** sob este Contrato:

            a)    realizar o pagamento do Preçoà **CONTRATADA** na forma e nos prazos aqui estabelecidos; e
            b)    fornecer as informações e todos os projetos e demais documentos necessários para a realização dos Serviços ora contratados.

    **9.    RESPONSABILIDADES**
        9.1.    A **CONTRATADA** , neste ato, se compromete a ressarcir integralmente todos os danos e despesas, inclusive, mas não se restringindo a, honorários advocatícios, que seus empregados, representantes, sócios/acionistas, administradores, diretores, prestadores de serviços em geral, prepostos e todos os indivíduos que, direta ou indiretamente, atuem sob sua responsabilidade ou orientação, eventualmente causarem à **CONTRATANTE** , em virtude de ato, fato, negócio, enfim, qualquer circunstância relacionada ao presente Contrato, incluindo perdas decorrentes de contingências trabalhistas.

        9.2.    A **CONTRATADA** declara, sob as penas da lei:

            a)    que não está impedida de desempenhar as atividades estipuladas no objeto do presente Contrato; e
            b)    estar em ordem junto aos Órgãos Públicos competentes, possuindo todas as licenças, autorizações e registros necessários para o regular exercício de suas atividades, bem como possuir capacitação técnica adequada para o cumprimento deste Contrato.

          9.2.1.    A **CONTRATADA** declara ser a única responsável perante as autoridades competentes e quaisquer terceiros pelo cumprimento de todas as normas legais vigentes em decorrência do objeto deste Contrato.

    **10.     PENALIDADES**

        10.1.   Qualquer atraso na conclusão dos Serviços por parte da **CONTRATADA** sujeitará a **CONTRATADA** às seguintes penalidades, sem prejuízo de outras previstas neste Contrato:

            a)    atraso entre 10 (dez) e 15 (quinze) dias corridos em relação à conclusão dos Serviços, será cobrada multa equivalente a 5% (cinco) do valor do item a ser entregue;
            b)    atraso entre 16 (dezesseis) e 20 (vinte) dias corridos em relação à conclusão dos Serviços, será cobrado multa equivalente a 10% (dez por cento) do valor do item a ser entregue;
            c)    atraso entre 21 (vinte e um) e 30 (trinta) dias corridos em relação à conclusão dos Serviços, será cobrado multa equivalente a 15% (dez por cento) do valor do item a ser entregue;
            d)    atraso superior a 31 (trinta e um) dias corridos à conclusão dos Serviços poderá referido Contrato ser rescindido, com aplicação da penalidade de 20% (vinte por cento) do valor total do Contrato, sendo devido à **CONTRATADA** o pagamento dos Serviços já realizados.

        10.2.   O descumprimento, por qualquer das Partes, de suas obrigações contratuais, acarretará à Parte inadimplente o pagamento de multa equivalente a 10% (dez por cento) do valor do total do Contrato, exceto se houver previsão de outra multa específica no Contrato.

    **11. DO SIGILO E DA CONFIDENCIALIDADE DAS INFORMAÇÕES**

        11.   A **CONTRATADA** se compromete, sob as penas da lei, em manter durante a vigência deste Contrato e pelo prazo de até 3 (três) anos contados do seu término (independentemente do motivo), o mais completo e absoluto sigilo sobre quaisquer dados, materiais, pormenores, informações, documentos, especificações técnicas e comerciais de produtos e serviços e outros, objeto deste instrumento, dos clientes ou de terceiros, de que venha a ter conhecimento ou acesso, ou que lhe venham a ser confiados, sejam relacionados ou não com a prestação/execução dos Serviços objeto deste Contrato.

        11.1.1.   A inobservância do disposto nesta cláusula acarretará sanções legais, por elas respondendo a **CONTRATADA** , no âmbito civil e criminal.

        11.2.   As Partes obrigam-se quanto aos Serviços objeto deste Contrato:

            a)    a manter sigilo, a qualquer tempo, inclusive após a extinção deste Contrato, sobre todas as informações, dados, materiais, pormenores, documentos, especificações técnicas e comerciais de produtos da **CONTRATANTE** ou de terceiros, de que venha ter conhecimento, acesso ou que lhe tenham sido confiados, que envolvam o objeto desta contratação, desde já classificadas como confidenciais, independentemente da forma como delas tiverem conhecimento; e
            b)    a devolver à outra Parte todo e qualquer material e documento, inclusive cópias, que lhe tenha sido entregue e/ou que tenha sido gerado por quaisquer das Partes em razão da prestação/execução do Contrato.

        11.3.   Todas as informações que a **CONTRATADA** vier a ter conhecimento serão utilizadas exclusivamente para a fiel execução deste Contrato e serão tratadas e garantidas como privadas e confidenciais.

        11.4.   A **CONTRATADA** reconhece que não poderá, a qualquer tempo, divulgar, ceder, doar ou transferir as informações, no todo ou em parte deste instrumento, para nenhuma outra pessoa, exceto quando as informações confidenciais ou parte delas necessitem ser divulgadas para seus empregados, dirigentes ou conselheiros que necessitem conhecê-las exclusivamente para a prestação/execução do presente Contrato.

        11.5.   Na hipótese de que a publicação ou a divulgação de informações confidenciais seja necessária por lei ou por qualquer órgão supervisor ou regulador, cujas exigências as partes contratantes e as pessoas a elas relacionadas tenham que cumprir, a **CONTRATADA** comunicará à outra **CONTRATANTE** tal exigência e as Partes deliberarão de comum acordo a respeito dos procedimentos a serem adotados, até a extensão permitida por tal legislação ou por tais regras, de modo a que as Partes possam adotar as medidas judiciais cabíveis e/ou dispensar a **CONTRATADA** do cumprimento das disposições desta cláusula do presente Contrato.

        11.6.   Em caso de descumprimento pela **CONTRATADA** de qualquer obrigação estabelecida nesta Clausula será imposta à **CONTRATADA** uma multa equivalente a 100% (cem por cento) do valor deste Contrato, multa esta não compensatória nem excludente de outras medidas cabíveis e já evocadas neste Instrumento, sem prejuízo das perdas e danos sofridos pela outra **CONTRATANTE**.

        11.7.   Fica expressamente vedada à **CONTRATADA** a utilização dos termos deste Contrato em divulgação ou publicidade, bem como, o uso do nome, marca e logomarca da **CONTRATANTE** e seus clientes, para qualquer finalidade e em qualquer meio de comunicação, quer seja na mídia impressa, escrita, falada ou eletrônica, sendo que a sua infração poderá ensejar a rescisão automática do presente Contrato, a critério da **CONTRATANTE** , além de sujeitar-se a **CONTRATADA** , ao pagamento de multa contratual e perdas e danos que forem apurados, porém, sem impedimento à informação e uso em seu portfólio de produtos e serviços, desde que mediante prévia autorização, por escrito, da **CONTRATANTE**.

    **12. DOS DIREITOS DE PROPRIEDADE INTELECTUAL**

        12.1.   Os direitos patrimoniais de autoria, direitos de exploração econômica e demais direitos de propriedade dos conteúdos resultantes dos Serviços tornar-se-ão propriedade exclusiva e indiscutível da **CONTRATANTE** , que poderá utilizá-los livremente, total ou parcialmente, na máxima extensão permitida em lei, sem qualquer ressalva, ônus, limitações, garantia real e/ou limitação temporal, de formato e de repetição, não cabendo à **CONTRATADA** qualquer direito ou remuneração em razão desta utilização, após o término deste Contrato.

        12.2.   A **CONTRATADA** garante por este Contrato que os métodos, técnicas e ferramentas de sua propriedade, utilizados durante a execução dos Serviços, incluindo os conteúdos resultantes da prestação dos Serviços, não infringem de nenhuma forma quaisquer direitos de propriedade intelectual e/ou imagem de terceiros, sendo responsável direto por qualquer eventual reclamação nesse sentido.

        12.3.   Caso os Serviços objeto deste Contrato sejam produzidos com exclusividade para a **CONTRATANTE** ou a seus clientes, a **CONTRATADA** , desde já, compromete-se a não copiar, reproduzir, divulgar, difundir, publicar ou utilizar, por qualquer meio ou método, os conteúdos resultantes dos Serviços objeto deste Contrato, sem a prévia e expressa autorização, por escrito, da **CONTRATANTE** , podendo esta considerar este Contrato rescindido de pleno direito, além de responder a **CONTRATADA** pelas perdas e danos que forem apurados. Pelas mesmas razões, poderá a **CONTRATANTE** , se assim desejar e a qualquer tempo, ampliar referidos conteúdos, alterá-los e/ou desenvolver novas funcionalidades, por conta própria ou mediante a contratação de terceiros sem que esta prática caracterize qualquer violação ao presente Contrato.

        12.4.   A **CONTRATADA** expressamente reconhece que as informações recebidas da **CONTRATANTE** são de propriedade da **CONTRATANTE** ou de seus clientes, e que esta não lhe concede, a respeito delas, nenhum tipo de licença expressa, implícita ou de qualquer outra natureza, nem tampouco direitos de propriedade intelectual, comprometendo-se, em consequência, a abster-se de tomar qualquer medida que possa prejudicar ou impedir o exercício de tais direitos.

        12.5.   As disposições desta Cláusula 12 são irrevogáveis e irretratáveis e vigorarão por prazo indeterminado.

    **13. DA RESILIÇÃO, ROMPIMENTO OU TÉRMINO**

        13.1.   Além das situações previstas em lei e neste instrumento, o presente Contrato será extinto de imediato e sem qualquer aviso, nas seguintes hipóteses por qualquer uma das Partes:

            a)    pedido de recuperação extrajudicial ou judicial ou falência por ou contra a outra Parte;
            b)    caso a outra Parte deixe de cumprir qualquer lei, decreto, portaria federal, estadual ou municipal, relacionada com os Serviços objeto deste Contrato;
            c)    a **CONTRATADA** tenha cassada sua autorização para a execução dos Serviços ora contratados; ou
            d)    suspensão, pela **CONTRATADA** , dos Serviços ora contratados por período superior a 15 (quinze) dias.

        13.2.   Ainda, a infração de qualquer das cláusulas ou condições estipuladas neste Contrato poderá ensejar a rescisão deste Contrato, por simples notificação escrita com indicação da denúncia à Parte infratora, que terá prazo de 5 (cinco) dias para sanar a falta. Decorrido o prazo e não tendo sido sanada a falta, o Contrato poderá ser rescindido de pleno direito pela parte prejudicada, respondendo ainda a Parte infratora pelas perdas e danos decorrentes e por todas as demais obrigações pactuadas neste instrumento.

        13.3.   Parte que der causa à rescisão deste Contrato sujeitar-se-á, sem prejuízo de outras sanções legais, ao pagamento à Parte inocente:

            a)    de multa correspondente a 20% (vinte por cento) do valor remanescente do Contrato; e
            b)    das perdas e danos diretos sofridos pela outra Parte em decorrência do descumprimento das suas obrigações contratuais ora avençadas.

        13.4.   Este Contrato poderá ser resilido a qualquer tempo pela **CONTRATANTE** mediante denúncia escrita com 30 (trinta) dias de antecedência pelo menos, período em que as Partes deverão cumprir regularmente com as obrigações ora assumidas.

        13.5.   Na hipótese de resilição/rescisão ou término deste Contrato, deverá a **CONTRATADA** devolver à **CONTRATANTE** todos os materiais e documentos que, eventualmente, encontrarem-se em seu poder.

        13.6.   Em qualquer hipótese de extinção deste Contrato, a **CONTRATANTE** apenas estará obrigada ao pagamento da remuneração da **CONTRATADA** até o último dia de efetiva prestação dos Serviços, inexistindo qualquer direito de garantia ao recebimento da remuneração por parte da **CONTRATADA** até o término do prazo de duração deste Contrato originalmente estabelecido.

    **14. SUBCONTRATAÇÃO, CESSÃO E TRANSFERÊNCIA DE DIREITOS**

        14.1.   É vedado à **CONTRATADA** transferir, onerar ou de qualquer forma dar em garantia o presente **CONTRATO** ou quaisquer direitos ou benefícios dele decorrentes.

        14.2.   É expressamente vedada a subcontratação dos Serviços a serem prestados pela **CONTRATADA** , sem a autorização expressa da **CONTRATANTE.**

        14.3.   Este Contrato e os respectivos direitos e obrigações não poderão ser cedidos por qualquer Parte, sem o consentimento prévio e expresso da outra Parte, sendo nulo e de nenhum efeito qualquer ato praticado em violação do disposto nesta Cláusula, exceto quanto à **CONTRATANTE** , que poderá ceder, sub-rogar ou transferir sua posição contratual total ou parcialmente, no que se refere a quaisquer dos direitos ou obrigações contidas no mesmo, para qualquer empresa do mesmo grupo econômico, quer seja sua controladora ou controlada ou coligada, cuja comunicação neste sentido será feita pela **CONTRATANTE** ao **CONTRATADO** posteriormente à realização dos atos acima.

    **15. DISPOSIÇÕES GERAIS**

        15.1.   Este Contrato e seu(s) anexo(s) constitui(em) o acordo integral entre as Partes no que tange ao seu objeto e substitui(em) qualquer outro acordo escrito ou verbal anteriormente convencionado pelas Partes (exceto eventuais termos ou contratos de confissão de dívida que estejam em vigor entre as Partes).  As disposições previstas no(s) anexo(s) devem ser interpretadas em harmonia com o disposto neste Contrato.  Em caso de conflito entre as disposições deste Contrato e aquelas de seu(s) anexo(s) prevalecerão as disposições deste Contrato.

        15.2.   A omissão ou tolerância das Partes, em exigir o estrito cumprimento dos termos e condições deste Contrato, não constituirá novação ou renúncia, nem afetará os seus direitos, que poderão ser exercidos a qualquer tempo. Se uma Parte não exercer seus direitos previstos neste Instrumento não significará renúncia ao mesmo.

        15.3.   Eventuais inclusões de outras cláusulas, exclusões ou alterações das já existentes, serão consignadas em aditivo, devidamente assinado pelas Partes, que passará a fazer parte integrante deste Contrato. Tudo o que não houver sido previsto neste instrumento deverá ser formalizado através de aditivos escritos e assinados pelas Partes.

        15.4.   Em nenhuma hipótese está a **CONTRATADA** autorizada a sacar títulos de crédito, letras de câmbio ou qualquer outro título cambiário com base neste Contrato. Da mesma forma, fica a **CONTRATADA** terminantemente proibida de dar em garantia, penhor ou caução quaisquer importâncias ou direitos recebíveis sob o presente Contrato.

        15.5.   As Partes são consideradas contratantes independentes e nada deste Contrato criará qualquer outro vínculo entre ambas, seja pelo aspecto empregatício, seja por quaisquer outros aspectos, tais como agente comercial, sociedade subsidiária, representação legal ou associação de negócios.

        15.6.   A **CONTRATADA** declara que possui plena capacidade para cumprir integralmente o objeto do presente instrumento, sem necessitar para tanto da realização de consideráveis investimentos.

        15.6.1.   Não obstante o disposto na Cláusula 15.6 acima, a **CONTRATADA** obriga-se a não realizar qualquer investimento considerável e relacionado ao objeto deste Contrato, sem a prévia concordância, por escrito, da **CONTRATANTE**. Assim, somente serão levados em consideração investimentos que forem objeto de concordância por parte da **CONTRATANTE** e que estiverem devidamente formalizados por meio de aditamento ao presente instrumento, realizado por escrito e assinado pelas partes, no qual deverão constar todos os critérios e regras para sua amortização.

        15.7.   Com referência aos Serviços ora contratados, fica acordado que a **CONTRATANTE** se reserva o direito de examinar e conduzir auditorias para verificara a regular prestação dos Serviços, sem a necessidade de notificação prévia à **CONTRATANTE** com respeito ao início da verificação.

        15.8.   Este Contrato constitui todo o entendimento e acordo entre as Partes e substitui todas as garantias, condições, promessas, declarações, contratos e acordos verbais ou escritos, anteriores sobre o objeto deste Contrato.

        15.9.   Fica estabelecido que qualquer despesa que a **CONTRATANTE** venha a ter relacionada aeventual reconhecimento de associação ou vínculo de emprego com a **CONTRATADA** ou qualquer de seus profissionais será reembolsada pela **CONTRATADA** à **CONTRATANTE** , ficando esta última desde já autorizada a reter da remuneração a quantia necessária à recomposição da perda incorrida.

        15.10.    As obrigações oriundas deste Contrato vinculam as Partes, seus herdeiros, sucessores e cessionários autorizados a qualquer título.

        15.11.    Quaisquer avisos ou comunicações entre as Partes, relativas ao presente Contrato, deverão ser encaminhadas por escrito, mediante envio de correio eletrônico (e-mail) e/ou por meio de carta registrada com comprovante de recebimento, nos endereços indicados nos itens I e II do Quadro Resumo deste Contrato.

        15.12.    Os gestores poderão realizar esclarecimentos, complementações e solucionar divergências surgidas, desde que não alterem as cláusulas e condições estabelecidas neste Contrato.

    **16. USO DE MÃO DE OBRA INFANTIL E OBRIGAÇÕES ANTICORRUPÇÃO**

        16.1.    A **CONTRATADA** obriga-se a não utilizar mão de obra infantil nos termos do artigo 403 da Consolidação das Leis do Trabalho, em harmonia com a Lei 8.069/90, combinadas com as disposições da Constituição Federal, tampouco mão de obra escrava ou compulsória.

        16.2.    A **CONTRATADA** , incluindo por intermédio de seus representantes, funcionários e agentes, declara que não violou as disposições: (i) da lei anticorrupção brasileira (Lei 12.846/13); (ii) da lei anticorrupção dos Estados Unidos de 1977 e aditamentos posteriores, conhecida como U.S. Foreign Corrupt Practices Act (FCPA); e (iii) da lei anticorrupção do Reino Unido de 2010, conhecida como U.K. Bribery Act (UKBA). A **CONTRATADA** , incluindo por intermédio de seus representantes, funcionários e agentes, não fez, e se compromete de forma irrevogável a não fazer, qualquer oferta, pagamento, promessa de pagamento ou autorização de pagamento de qualquer valor ou coisa de valor a um agente público, ou ainda a qualquer pessoa sabendo que todo ou parte daquele valor seria oferecido, dado ou prometido por tal pessoa a um agente público, com propósito de: (i) influenciar qualquer ato ou decisão desse agente público ou induzir tal agente público a realizar ou omitir qualquer ato em violação de seu dever legítimo ou oficial; (ii) induzir tal agente público a usar sua influência com o governo ou qualquer de seus órgãos para afetar ou influenciar qualquer ato ou decisão desse governo ou órgão; ou (iii) obter ou reter negócios para qualquer pessoa.

        16.3.    Caso venha a ser comprovado que a **CONTRATADA** incorreu nas hipóteses destacadas acima, ficará esta responsável por todos os danos diretos e indiretos que venha causar à **CONTRATANTE** por sua ação ou omissão.

    **17. SOLUÇÃO DE CONTROVÉRSIAS**

        17.1.    As Partes comprometem-se a envidar seus melhores esforços para resolver, amigavelmente e de boa fé, quaisquer demandas, divergências e outras questões relativas ao objeto deste Contrato, tão logo quanto possível, através de negociações diretas.

        17.2.    Fica eleito para a solução de controvérsias o foro da cidade de ${ title_case(comarca | lower) }/${ estado_comarca }, com a renúncia de qualquer outro, por mais privilegiado que seja.

    ${ title_case(comarca) }, ${ dataAssinatura }.

    **Contratante(s):**

    % for item in contratante:

    ____________________________________________
    **${ item.name.first }**
    CNPJ: ${ item.cnpj }
    % endfor

    **Contratada(s):**

    % for item in contratada:

    ____________________________________________
    **${ item.name.first }**
    % if item.tipo_pessoa == 'Física':
    **${ item.cpf }**
    % else:
    **${ item.cnpj }**
    % endif
    % endfor

    **Testemunhas:**

    | 1. _______________________________ | 2. _______________________________ |
    | --- | --- |
    | Nome:                              | Nome:                              |
      CPF:                                 CPF:
     
    % if temAnexo:
    % for item in anexos:
    ${ item }
    % endfor
    % endif