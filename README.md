# 8bit

            	 0     1     2     3     4     5     6     7     8     9     10    11    12    13    14    15
        ADDRESS: MS2   MS1   MS0   I3    I2    I1    I0    CF    ZF    X     X     X     X     X     X     X

        I/O E1 : HLT   MI    RI    RO    IO    II    AI    AO
        I/O E2 : EO    ADD   SU    SHL   SHR   XOR   NOT   AND
        I/O E3 : OR    BI    BO    OI    CE    CO    J     FI
        I/O E4 : DI    DO    RMS   CLR   X     X     X     X



        NOP =  0b10000000000000000000000000000000
        HLT =  0b10000000000000000000000000000000
        MI  =  0b01000000000000000000000000000000
        RI  =  0b00100000000000000000000000000000
        RO  =  0b00010000000000000000000000000000
        IO  =  0b00001000000000000000000000000000
        II  =  0b00000100000000000000000000000000
        AI  =  0b00000010000000000000000000000000
        AO  =  0b00000001000000000000000000000000
        EO  =  0b00000000100000000000000000000000
        ADD =  0b00000000010000000000000000000000
        SU  =  0b00000000001000000000000000000000
        SHL =  0b00000000000100000000000000000000
        SHR =  0b00000000000010000000000000000000
        XOR =  0b00000000000001000000000000000000
        NOT =  0b00000000000000100000000000000000
        AND =  0b00000000000000010000000000000000
        OR  =  0b00000000000000001000000000000000
        BI  =  0b00000000000000000100000000000000
        BO  =  0b00000000000000000010000000000000
        OI  =  0b00000000000000000001000000000000
        CE  =  0b00000000000000000000100000000000
        CO  =  0b00000000000000000000010000000000
        J   =  0b00000000000000000000001000000000
        FI  =  0b00000000000000000000000100000000
        DI  =  0b00000000000000000000000010000000
        DO  =  0b00000000000000000000000001000000
        RMS =  0b00000000000000000000000000100000
        CLR =  0b00000000000000000000000000010000
        X1  =  0b00000000000000000000000000001000
        X2  =  0b00000000000000000000000000000100
        X3  =  0b00000000000000000000000000000010
        X4  =  0b00000000000000000000000000000001
        
                  T0
        FETCH1 =  MI|CO
                  T1
        FETCH2 =  RO|II|CE
               T2                   T3                      T4   T5   T6   T7
          ----------------------------------------------------------------------------------------------------
        NJC = [NOP,                 RMS,                    RMS, RMS, RMS, RMS] # -1 | if conditional jump is false
        LDA = [IO | MI,             RO | AI,                RMS, RMS, RMS, RMS] # 0  |
        STA = [IO | MI,             AO | RI,                RMS, RMS, RMS, RMS] # 1  |
        LDI = [IO | AI,             RMS,                    RMS, RMS, RMS, RMS] # 2  |
        ADD = [IO | MI, RO | BI,    ADD | EO | AI | FI,     RMS, RMS, RMS, RMS] # 3  |
        SUB = [IO | MI, RO | BI,    SU  | EO | AI | FI,     RMS, RMS, RMS, RMS] # 4  |
        AND = [IO | MI, RO | BI,    AND | EO | AI | FI,     RMS, RMS, RMS, RMS] # 5  |
        OR  = [IO | MI, RO | BI,    OR  | EO | AI | FI,     RMS, RMS, RMS, RMS] # 6  |
        XOR = [IO | MI, RO | BI,    XOR | EO | AI | FI,     RMS, RMS, RMS, RMS] # 7  |
        NOT = [NOT | EO | AI | FI,  RMS,                    RMS, RMS, RMS, RMS] # 8  |
        SHL = [SHL | EO | AI | FI,  RMS,                    RMS, RMS, RMS, RMS] # 9  |
        SHR = [SHR | EO | AI | FI,  RMS,                    RMS, RMS, RMS, RMS] # 10 |
        JMP = [IO | J,              RMS,                    RMS, RMS, RMS, RMS] # 11 |
        JC  = [IO | J,              RMS,                    RMS, RMS, RMS, RMS] # 12 |
        JZ  = [IO | J,              RMS,                    RMS, RMS, RMS, RMS] # 13 |
        OUT = [AO | OI,             RMS,                    RMS, RMS, RMS, RMS] # 14 |
        HLT = [HLT,                 HLT,                    HLT, HLT, HLT, HLT] # 15 |
        
        
           operations    0000    0001    0010    0011    0100    0101    0110    0111    1000    1001    1010    1011    1100    1101    1110    1111
        OPPLIST   =    [LDA,    STA,    LDI,    ADD,    SUB,    AND,    OR,     XOR,    NOT,    SHL,    SHR,    JMP,    JC,     JZ,     OUT,    HLT ]

