.. -----------------------------------------------------------------------------
   ..
   ..  Filename       : index.rst
   ..  Author         : Huang Leilei
   ..  Status         : draft
   ..  Created        : 2022-03-28
   ..  Description    : template
   ..
.. -----------------------------------------------------------------------------

Template
========

Header
------

CALC_DIV.hpp
````````````````

    ::

        //------------------------------------------------------------------------------
            //
            //  Filename       : calc_div.hpp
            //  Author         : Huang Leilei
            //  Status         : draft
            //  Created        : 2022-03-28
            //  Description    : divider related headers
            //
        //------------------------------------------------------------------------------

        #ifndef __CALC_DIV_HPP__
        #define __CALC_DIV_HPP__

        //*** INCLUDE ******************************************************************
            #include "calc_unit.hpp"


        //*** DEFINE *******************************************************************


        //*** CLASS ********************************************************************
        // CALC_DIV
        class CALC_DIV: public CALC_UNIT
        {
        //--- PRIVATE ENUMERATOR ---------------
        private:


        //--- PRIVATE VARIABLE -----------------
        private:
            // connection
                CALC_UNIT *m_unitPrev;

            // information
                //...

            // data
                //...

            // cost
                //...

            // debug
                //...


        //--- PRIVATE FUNCTION -----------------
        private:
            // load
                virtual void loadPipe();
              //virtual void loadFile();
              //virtual void loadRand();

            // process
              //virtual void procPrev();
                virtual void procCore();
                virtual void procPost();

                inline void procCoreDiv() {
                    for (int k = 0; k < m_cfg->sizUnitZ; ++k) {
                        for (int j = 0; j < m_cfg->sizUnitY; ++j) {
                            for (int i = 0; i < m_cfg->sizUnitX; ++i) {
                                // core
                                (*m_datOut)[k][j][i] = calc_getDatDiv(m_cfg->addFlgSaturation, (*m_datInp0)[k][j][i], (*m_datInp1)[k][j][i]);
                                // log
                                if ((calc_enmInfo_t)m_cfg->enmInfo >= calc_enmInfo_t::COMMON) {
                                    printf("    %02d-%04d-%04d: 0x%04x * 0x10000 / 0x%04x = 0x%04x\n", k, j, i,
                                        (*m_datInp0)[k][j][i] & 0xffff,
                                        (*m_datInp1)[k][j][i] & 0xffff,
                                        (*m_datOut )[k][j][i] & 0xffff
                                    );
                                }
                            }
                        }
                    }
                }

            // dump
              //virtual void dumpFile();


        //--- PUBLIC FUNCTION ------------------
        public:
            // basic
                CALC_DIV();
              //~CALC_DIV();
                virtual void connect(calc_cfg_t &cfg, CALC_FTH &fth, CALC_DMP &dmp, CALC_UNIT &unit);
        };

        #endif /* __CALC_DIV_HPP__ */


Source
------

CALC_DIV.cpp
````````````````

    ::

        //------------------------------------------------------------------------------
            //
            //  Filename       : calc_div.cpp
            //  Author         : Huang Leilei
            //  Status         : draft
            //  Created        : 2022-03-28
            //  Description    : divider related codes (top)
            //
        //------------------------------------------------------------------------------

        //*** INCLUDE ******************************************************************
        #include "calc_div.hpp"


        //*** FUNCTION *****************************************************************
        // CALC_DIV
        CALC_DIV::CALC_DIV()
        {
            // identification
            m_strTag = "CALC_DIV";
        }

        // ~CALC_DIV
        //CALC_DIV::~CALC_DIV()
        //{
        //    // delete
        //    //...
        //}

        // connect
        void CALC_DIV::connect(
        calc_cfg_t &cfg, CALC_FTH &fth, CALC_DMP &dmp, CALC_UNIT &unit)
        {
            // basic
            CALC_UNIT::connect(cfg, fth, dmp);

            // modules
            m_unitPrev = &unit;

            // configuration
            m_cfgFlgProc =                 m_cfg->divFlgProc;
            m_cfgEnmLoad = (calc_enmLoad_t)m_cfg->divEnmLoad;
        }


CALC_DIV_load.cpp
`````````````````````

    ::

        //------------------------------------------------------------------------------
            //
            //  Filename       : calc_div_load.cpp
            //  Author         : Huang Leilei
            //  Status         : draft
            //  Created        : 2022-03-28
            //  Description    : divider related codes (load)
            //
        //------------------------------------------------------------------------------

        //*** INCLUDE ******************************************************************
        #include "calc_div.hpp"


        //*** FUNCTION *****************************************************************
        // loadPipe
        void CALC_DIV::loadPipe()
        {
            // basic
            CALC_UNIT::loadPipe();

            // data
            m_unitPrev->cpyDatOut(*m_datInp1);
        }

        // loadFile
        //void CALC_DIV::loadFile()
        //{
        //    // basic
        //    CALC_UNIT::loadFile();
        //
        //    //...
        //}

        //// loadRand
        //void CALC_DIV::loadRand()
        //{
        //    // basic
        //    CALC_UNIT::loadRand();
        //
        //    //...
        //}

CALC_DIV_proc.cpp
`````````````````````

    ::

        //------------------------------------------------------------------------------
            //
            //  Filename       : calc_div_proc.cpp
            //  Author         : Huang Leilei
            //  Status         : draft
            //  Created        : 2022-03-28
            //  Description    : divider related codes (proc)
            //
        //------------------------------------------------------------------------------

        //*** INCLUDE ******************************************************************
        #include "calc_div.hpp"


        //*** FUNCTION *****************************************************************
        // procPrev
        //void CALC_DIV::procPrev()
        //{
        //    // basic
        //    CALC_UNIT::procPrev();
        //
        //    // for the first unit
        //    static bool flag = 1;
        //    if (flag) {
        //        // clear flag
        //        flag = 0;
        //
        //        //...
        //    }
        //
        //    // for the first unit in each frame
        //    if (m_cfg->idxUnitX == 0 && m_cfg->idxUnitY == 0) {
        //        //...
        //    }
        //
        //    // for each unit
        //    {
        //        //...
        //    }
        //}

        // procCore
        void CALC_DIV::procCore()
        {
            procCoreDiv();
        }

        // procPost
        void CALC_DIV::procPost()
        {
            // basic
            CALC_UNIT::procPost();

            // for the first unit
            static bool flag = 1;
            if (flag) {
                // clear flag
                flag = 0;

                //...
            }

            // for the first unit in each frame
            if (m_cfg->idxUnitX == 0 && m_cfg->idxUnitY == 0) {
                //...
            }

            // for each unit
            {
                m_dmp->setDatOut(*m_cfg, *m_datOut);
            }
        }

CALC_DIV_dump.cpp
`````````````````````

    ::

        //------------------------------------------------------------------------------
            //
            //  Filename       : calc_div_dump.cpp
            //  Author         : Huang Leilei
            //  Status         : draft
            //  Created        : 2022-03-28
            //  Description    : divider related codes (dump)
            //
        //------------------------------------------------------------------------------

        //*** INCLUDE ******************************************************************
        #include "calc_div.hpp"


        //*** FUNCTION *****************************************************************
        // dumpFile
        //void CALC_DIV::dumpFile()
        //{
        //    // basic
        //    CALC_UNIT::dumpFile();
        //
        //    //...
        //}
