# robot
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>방과후 강사 채용 점수 협업 시뮬레이터</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        primary: '#1D4ED8', // Blue 700
                        secondary: '#F59E0B', // Amber 500
                        background: '#F9FAFB', // Gray 50
                    }
                }
            }
        }
    </script>
    <style>
        .score-input {
            width: 100%;
            padding: 8px;
            border: 1px solid #D1D5DB;
            border-radius: 6px;
            text-align: center;
            font-weight: 500;
        }
        .text-input-area {
            width: 100%;
            min-height: 150px; 
            padding: 10px;
            border: 1px solid #D1D5DB;
            border-radius: 6px;
            resize: vertical;
            font-size: 0.875rem; /* text-sm */
        }
        .rubric-item {
            margin-bottom: 12px;
            padding: 8px 0;
            border-bottom: 1px dashed #E5E7EB;
        }
    </style>
</head>
<body class="bg-background min-h-screen p-4 md:p-8 font-sans">

    <div class="max-w-5xl mx-auto bg-white shadow-xl rounded-xl p-6 md:p-10">
        <h1 class="text-3xl font-bold text-gray-800 mb-6 border-b pb-3 text-center">
            강사 채용 점수 협업 시뮬레이터 (빈 양식)
        </h1>
        <p class="text-gray-600 mb-8 text-center">
            **입력 칸이 모두 비어 있습니다.** 서류 내용을 작성하고 '총 점수 계산'을 눌러 만점을 목표로 해보세요!
        </p>

        <div class="grid lg:grid-cols-3 gap-8">
            
            <!-- 1. 정량 평가 (총 50점) -->
            <div class="lg:col-span-1 bg-blue-50 p-6 rounded-lg border-2 border-blue-200 h-full">
                <h2 class="text-xl font-semibold text-blue-800 mb-4">1. 정량 평가 (50점 만점)</h2>
                <p class="text-sm text-gray-600 mb-4 font-bold">서류 제출 시 확정되는 점수 영역입니다. (현재 최소 점수 적용)</p>
                
                <div class="space-y-6">
                    <!-- 강사 자격 (20점) -->
                    <div>
                        <h3 class="font-bold text-gray-700 mb-2 border-b border-blue-200 pb-1">① 강사 자격 (20점)</h3>
                        
                        <div class="rubric-item">
                            <label for="majorStatus" class="text-sm font-medium block">전공 이수 여부 (Max 10점):</label>
                            <select id="majorStatus" class="score-input bg-white text-sm">
                                <option value="10">대학원 전공 이수 (10점)</option>
                                <option value="9">대학교 전공 이수 (9점)</option>
                                <option value="8" selected>비전공 (8점)</option>
                            </select>
                        </div>

                        <div class="rubric-item">
                            <label for="certificateCount" class="text-sm font-medium block">관련 자격증 개수 (Max 10점):</label>
                            <select id="certificateCount" class="score-input bg-white text-sm">
                                <option value="10">2개 이상 (10점)</option>
                                <option value="9">1개 (9점)</option>
                                <option value="8" selected>무 (8점)</option>
                            </select>
                        </div>
                    </div>

                    <!-- 강사 경력 (30점) -->
                    <div>
                        <h3 class="font-bold text-gray-700 mb-2 border-b border-blue-200 pb-1">② 강사 경력 (30점)</h3>
                        
                        <div class="rubric-item">
                            <label for="careerPeriod" class="text-sm font-medium block">관련 프로그램 운영 경력 (Max 20점):</label>
                            <select id="careerPeriod" class="score-input bg-white text-sm">
                                <option value="20">5년 이상 (20점)</option>
                                <option value="18">3년 이상 ~ 5년 미만 (18점)</option>
                                <option value="16">1년 이상 ~ 3년 미만 (16점)</option>
                                <option value="14">1년 미만 (14점)</option>
                                <option value="13" selected>없음 (13점)</option>
                            </select>
                        </div>

                        <div class="rubric-item flex items-center justify-between">
                            <label for="careerDiversity" class="text-sm font-medium">활동 경력의 다양성/전문성 (Max 5점):</label>
                            <div class="flex items-center space-x-2">
                                <input type="checkbox" id="careerDiversity" class="h-4 w-4 text-blue-600 border-gray-300 rounded">
                                <span class="text-sm text-gray-700 font-semibold">5점</span>
                            </div>
                        </div>

                        <div class="rubric-item flex items-center justify-between">
                            <label for="awardRecord" class="text-sm font-medium">개인 수상 및 학생 지도 실적 (Max 5점):</label>
                            <select id="awardRecord" class="score-input bg-white w-24 text-sm">
                                <option value="5">유 (5점)</option>
                                <option value="2" selected>무 (2점)</option>
                            </select>
                        </div>
                    </div>
                </div>
            </div>

            <!-- 2. 정성 평가 (총 40점) -->
            <div class="lg:col-span-2 space-y-6">
                <div class="bg-yellow-50 p-6 rounded-lg border-2 border-yellow-200">
                    <h2 class="text-xl font-semibold text-yellow-800 mb-2">2. 정성 평가 (40점 만점)</h2>
                    <p class="text-sm text-gray-600 mb-4">운영 계획(25점), 교재/콘텐츠(5점), 적합성(10점)으로 점수가 산출됩니다. (최소 90% 글자 수 및 키워드 충족 시 만점)</p>
                </div>

                <!-- 2.1 운영 목표 (운영 계획 8점) -->
                <div class="p-4 border border-gray-200 rounded-lg bg-white">
                    <label for="textQual1_Goal" class="text-lg font-bold text-gray-800 block mb-2">
                        2.1. 운영 목표 (<span class="text-yellow-600" id="score_display_textQual1_Goal">8점/<span class="text-red-600">0.00점</span></span>):
                        <span class="text-sm font-normal text-primary" id="char_count_textQual1_Goal">(500자 이내) (현재 0자)</span>
                    </label>
                    <p class="text-xs text-gray-500 mb-2">학생 역량 기술 및 초등 심리와 발달 정도를 고려한 목표 기술 필수 (최소 450자 권장).</p>
                    <textarea id="textQual1_Goal" class="text-input-area" placeholder="[필수 키워드] 학생 역량, 초등 심리, 발달 정도, 구체적 목표, 흥미 유발."></textarea>
                </div>

                <!-- 2.2 운영 내용과 방법 (운영 계획 12점) -->
                <div class="p-4 border border-gray-200 rounded-lg bg-white">
                    <label for="textQual2_Method" class="text-lg font-bold text-gray-800 block mb-2">
                        2.2. 운영 내용/방법 (<span class="text-yellow-600" id="score_display_textQual2_Method">12점/<span class="text-red-600">0.00점</span></span>):
                        <span class="text-sm font-normal text-primary" id="char_count_textQual2_Method">(2000자 이내) (현재 0자)</span>
                    </label>
                    <p class="text-xs text-gray-500 mb-2">수준별/학년별 내용, 연간 계획, 안전 지도, 차별화 전략, 구체적 강의 방법 포함 필수 (최소 1800자 권장).</p>
                    <textarea id="textQual2_Method" class="text-input-area" placeholder="[필수 키워드] 수준별 교육, 학년 구분, 연간 지도 계획, 안전 지도 계획, 차별화 전략, 구체적 강의 방법, 학생 참여."></textarea>
                </div>

                <!-- 2.3 평가 방법 (운영 계획 5점) -->
                <div class="p-4 border border-gray-200 rounded-lg bg-white">
                    <label for="textQual3_Eval" class="text-lg font-bold text-gray-800 block mb-2">
                        2.3. 평가 방법 (<span class="text-yellow-600" id="score_display_textQual3_Eval">5점/<span class="text-red-600">0.00점</span></span>):
                        <span class="text-sm font-normal text-primary" id="char_count_textQual3_Eval">(500자 이내) (현재 0자)</span>
                    </label>
                    <p class="text-xs text-gray-500 mb-2">평가 내용, 횟수, 방법(상세 기술), 피드백 계획 포함 필수 (최소 450자 권장).</p>
                    <textarea id="textQual3_Eval" class="text-input-area" placeholder="[필수 키워드] 평가 내용, 평가 횟수, 평가 방법 상세, 피드백 계획, 과정 중심, 루브릭."></textarea>
                </div>
                
                <!-- 2.4 교재, 콘텐츠 (5점) -->
                <div class="p-4 border border-gray-200 rounded-lg bg-white">
                    <label for="textQual4_Material" class="text-lg font-bold text-gray-800 block mb-2">
                        2.4. 교재, 콘텐츠 (<span class="text-yellow-600" id="score_display_textQual4_Material">5점/<span class="text-red-600">0.00점</span></span>):
                        <span class="text-sm font-normal text-primary" id="char_count_textQual4_Material">(500자 이내) (현재 0자)</span>
                    </label>
                    <p class="text-xs text-gray-500 mb-2">교구명/제조사/가격, 선정 이유(구체적), 재료비 예정가격 포함 필수 (최소 450자 권장).</p>
                    <textarea id="textQual4_Material" class="text-input-area" placeholder="[필수 키워드] 교구명, 출판사/제조사, 가격, 선정 이유 구체성, 재료비 예정가격."></textarea>
                </div>

                <!-- 2.5 적합성 (자기소개서) (10점) -->
                <div class="p-4 border border-gray-200 rounded-lg bg-white">
                    <label for="textQual5_Self" class="text-lg font-bold text-gray-800 block mb-2">
                        2.5. 적합성/자기소개서 (<span class="text-yellow-600" id="score_display_textQual5_Self">10점/<span class="text-red-600">0.00점</span></span>):
                        <span class="text-sm font-normal text-primary" id="char_count_textQual5_Self">(1500자 이내) (현재 0자)</span>
                    </label>
                    <p class="text-xs text-gray-500 mb-2">방과후학교 이해도, 열정, 학생에 대한 이해, 사명감 등을 포함하여 작성 필수 (최소 1350자 권장).</p>
                    <textarea id="textQual5_Self" class="text-input-area" placeholder="[필수 키워드] 방과후학교 이해도, 생활 태도/열정, 학생 이해와 사랑, 사명감, 청렴"></textarea>
                </div>
            </div>

        </div>

        <button onclick="calculateScore()" class="w-full mt-8 py-3 bg-primary hover:bg-blue-800 text-white font-bold rounded-lg transition duration-200">
            총 점수 계산 및 상세 피드백 확인 (총점 90점)
        </button>

        <!-- 결과 표시 영역 -->
        <div id="resultContainer" class="mt-8 p-6 bg-gray-50 border-2 border-gray-200 rounded-lg hidden">
            <h2 class="text-2xl font-bold text-gray-800 mb-4 text-center">최종 점수 분석 (90점 만점)</h2>
            <div class="flex justify-around items-center mb-6 flex-wrap gap-4">
                <div class="text-center">
                    <p class="text-lg text-blue-600 font-semibold">정량 점수 (50점)</p>
                    <p id="quantitativeScore" class="text-4xl font-extrabold text-blue-800">0.0</p>
                </div>
                <div class="text-center">
                    <p class="text-lg text-yellow-600 font-semibold">정성 점수 (40점)</p>
                    <p id="qualitativeScore" class="text-4xl font-extrabold text-yellow-800">0.0</p>
                </div>
                <div class="text-center">
                    <p class="text-lg text-primary font-semibold">최종 총점</p>
                    <p id="totalScore" class="text-5xl font-extrabold text-primary">0.0</p>
                </div>
            </div>

            <!-- 시뮬레이션 분석 메시지 -->
            <div id="simulationMessage" class="mt-4 p-4 rounded-md text-center"></div>
        </div>

        <!-- 상세 피드백 영역 -->
        <div id="detailedFeedbackContainer" class="mt-8 hidden">
            <h2 class="text-xl font-bold text-gray-800 border-b pb-2 mb-4">정성 평가 항목별 상세 피드백</h2>
        </div>
    </div>

    <script>
        // 정성 평가 항목별 상세 설정 (최대 점수, 최대 길이, 강사님 요청 최소 길이: 90% 기준)
        const QUALITATIVE_FIELDS = {
            textQual1_Goal: { maxScore: 8, maxLength: 500, minLength: 450, label: '운영 목표' },
            textQual2_Method: { maxScore: 12, maxLength: 2000, minLength: 1800, label: '운영 내용/방법' },
            textQual3_Eval: { maxScore: 5, maxLength: 500, minLength: 450, label: '평가 방법' },
            textQual4_Material: { maxScore: 5, maxLength: 500, minLength: 450, label: '교재, 콘텐츠' },
            textQual5_Self: { maxScore: 10, maxLength: 1500, minLength: 1350, label: '적합성/자기소개서' }, // 1500자의 90%
        };

        const RUBRIC = {
            MAX_QUANTITATIVE: 50,
            
            // 텍스트 분석 배점 비율
            SCORE_BASE_RATIO: 0.4,      
            SCORE_KEYWORD_RATIO: 0.4,   
            SCORE_STRUCTURE_RATIO: 0.2, 
            
            RUBRIC_KEYWORDS: {
                textQual1_Goal: ['학생 역량', '초등 심리', '발달 정도', '구체적 목표', '흥미 유발'],
                textQual2_Method: ['수준별 교육', '학년 구분', '연간 지도 계획', '안전 지도 계획', '차별화 전략', '구체적 강의 방법', '학생 참여'],
                textQual3_Eval: ['평가 내용', '평가 횟수', '평가 방법 상세', '피드백 계획', '과정 중심', '루브릭'],
                textQual4_Material: ['교구명', '출판사/제조사', '가격', '선정 이유 구체성', '재료비 예정가격'],
                textQual5_Self: ['방과후학교 이해도', '생활 태도/열정', '학생 이해와 사랑', '사명감', '청렴']
            }
        };

        function calculateQuantitativeScore() {
            const majorScore = parseInt(document.getElementById('majorStatus').value) || 0;
            const certScore = parseInt(document.getElementById('certificateCount').value) || 0;
            const careerPeriodScore = parseInt(document.getElementById('careerPeriod').value) || 0;
            const diversityScore = document.getElementById('careerDiversity').checked ? 5 : 0;
            const awardScore = parseInt(document.getElementById('awardRecord').value) || 0;
            const totalQuantitative = majorScore + certScore + careerPeriodScore + diversityScore + awardScore;
            
            return Math.min(totalQuantitative, RUBRIC.MAX_QUANTITATIVE); 
        }

        /**
         * 텍스트 내용을 분석하여 정성 점수와 상세 피드백을 반환합니다.
         */
        function analyzeTextScore(id, maxScore) {
            const text = document.getElementById(id).value;
            const keywords = RUBRIC.RUBRIC_KEYWORDS[id];
            const { minLength } = QUALITATIVE_FIELDS[id]; // 강사님 요청 최소 길이 사용
            let score = 0;
            const normalizedText = text.replace(/\s+/g, '').trim(); 
            const feedback = {
                base: { max: maxScore * RUBRIC.SCORE_BASE_RATIO, score: 0, reason: '' },
                keyword: { max: maxScore * RUBRIC.SCORE_KEYWORD_RATIO, score: 0, reason: '', found: [], missing: [] },
                structure: { max: maxScore * RUBRIC.SCORE_STRUCTURE_RATIO, score: 0, reason: '' }
            };

            // 1. 기본 점수 (글자 수 - 강사님 요청의 엄격한 최소 기준 적용)
            if (normalizedText.length >= minLength) {
                feedback.base.score = feedback.base.max;
                feedback.base.reason = `(통과) 강사님 요청 최소 글자수(${minLength}자) 충족.`;
            } else if (normalizedText.length > 0) {
                 // 최소 길이 미달 시 길이 비율에 따라 점수 부여
                 feedback.base.score = feedback.base.max * (normalizedText.length / minLength); 
                 feedback.base.reason = `(미달) 강사님 요청 최소 글자수(${minLength}자)에 미달하여 길이 비율(${normalizedText.length}/${minLength})에 따라 부분 점수 부여.`;
            } else {
                 feedback.base.reason = '(미작성) 내용이 비어있습니다.';
            }
            score += feedback.base.score;

            // 2. 키워드 포함 점수
            let keywordCount = 0;
            keywords.forEach(keyword => {
                if (text.includes(keyword)) {
                    keywordCount++;
                    feedback.keyword.found.push(keyword);
                } else {
                    feedback.keyword.missing.push(keyword);
                }
            });
            
            if (keywords.length > 0) {
                const keywordRatio = keywordCount / keywords.length;
                feedback.keyword.score = keywordRatio * feedback.keyword.max;
                
                feedback.keyword.reason = `(키워드 적중률 ${keywordCount}/${keywords.length}) 획득.`;
                if (feedback.keyword.missing.length > 0) {
                    feedback.keyword.reason += ` 미반영 키워드: [${feedback.keyword.missing.join(', ')}]`;
                }
            }
            score += feedback.keyword.score;

            // 3. 구조화/가독성 점수
            const structureRegex = /[\n\r]{2,}|[-\*]|\d+\.\s/; // 2회 이상의 줄바꿈, 목록 기호 등
            // 키워드가 100% 충족되고, 엄격한 최소 글자수가 충족되었으며, 2회 이상의 줄바꿈 또는 목록 기호가 사용된 경우 만점
            if (keywordCount === keywords.length && normalizedText.length >= minLength && structureRegex.test(text)) {
                 feedback.structure.score = feedback.structure.max;
                 feedback.structure.reason = '(만점) 모든 조건을 충족한 완벽한 구조.';
            } else if (structureRegex.test(text) && normalizedText.length > minLength / 2) {
                feedback.structure.score = feedback.structure.max;
                feedback.structure.reason = '(통과) 명확한 단락 구분 또는 목록 기호를 사용하여 가독성 우수.';
            } else {
                feedback.structure.reason = '(부족) 단락 구분(줄 바꿈 2회 이상) 또는 목록 기호가 없어 가독성이 낮다고 판단됨.';
            }
            score += feedback.structure.score;
            
            const finalScore = parseFloat(Math.min(score, maxScore).toFixed(2));
            return { score: finalScore, feedback };
        }

        /**
         * 개별 정성 점수를 계산하고, 화면에 표시합니다.
         */
        function calculateQualitativeScores() {
            const results = {};
            let totalQualitative = 0;

            for (const id in QUALITATIVE_FIELDS) {
                const { maxScore } = QUALITATIVE_FIELDS[id];
                const result = analyzeTextScore(id, maxScore);
                results[id] = result;
                totalQualitative += result.score;

                // 점수 표시 업데이트 (MaxScore/CalculatedScore)
                const scoreDisplay = document.getElementById(`score_display_${id}`);
                if (scoreDisplay) {
                    const formattedScore = result.score.toFixed(2);
                    // 만점일 경우 초록색, 아니면 빨간색
                    const colorClass = (result.score === maxScore) ? 'text-green-600' : 'text-red-600'; 
                    scoreDisplay.innerHTML = `${maxScore}점/<span class="${colorClass} font-extrabold">${formattedScore}점</span>`;
                }
            }
            
            return { scores: results, total: parseFloat(totalQualitative.toFixed(2)) };
        }

        function updateCharCount(id) {
            const textarea = document.getElementById(id);
            const text = textarea.value;
            const currentLength = text.length; 
            const { maxLength } = QUALITATIVE_FIELDS[id];

            // 실시간으로 점수도 업데이트하여 즉각적인 피드백 제공 (간이 계산)
            const result = analyzeTextScore(id, QUALITATIVE_FIELDS[id].maxScore);
            const scoreDisplay = document.getElementById(`score_display_${id}`);
            const formattedScore = result.score.toFixed(2);
            const colorClass = (result.score === QUALITATIVE_FIELDS[id].maxScore) ? 'text-green-600' : 'text-red-600';
            scoreDisplay.innerHTML = `${QUALITATIVE_FIELDS[id].maxScore}점/<span class="${colorClass} font-extrabold">${formattedScore}점</span>`;


            const charCountDisplay = document.getElementById(`char_count_${id}`);
            if (charCountDisplay) {
                const colorClass = (currentLength > maxLength) ? 'text-red-600 font-bold' : 'text-primary';
                charCountDisplay.innerHTML = `(${maxLength}자 이내) (<span class="${colorClass}">현재 ${currentLength}자</span>)`;
            }
        }

        function renderDetailedFeedback(results) {
            const container = document.getElementById('detailedFeedbackContainer');
            container.innerHTML = `<h2 class="text-xl font-bold text-gray-800 border-b pb-2 mb-4">정성 평가 항목별 상세 피드백</h2>`;
            container.classList.remove('hidden');

            for (const id in results) {
                const { score, feedback } = results[id];
                const { maxScore, label } = QUALITATIVE_FIELDS[id];
                
                // 항목 제목
                let html = `
                    <div class="bg-white p-4 rounded-lg shadow-md mb-4 border-l-4 ${score === maxScore ? 'border-green-500' : 'border-red-500'}">
                        <h3 class="text-lg font-bold text-gray-800 mb-2">${label} (${maxScore}점 만점)</h3>
                        <p class="text-2xl font-extrabold mb-3 inline-block pr-4">획득 점수: 
                            <span class="${score === maxScore ? 'text-green-600' : 'text-red-600'}">${score.toFixed(2)}점</span>
                        </p>
                        <div class="space-y-2 text-sm">
                            <div class="p-2 border rounded-md bg-gray-50">
                                <span class="font-semibold text-gray-700">① 기본 점수 (Max ${feedback.base.max.toFixed(1)}점):</span> 
                                <span class="text-gray-600">${feedback.base.score.toFixed(2)}점. ${feedback.base.reason}</span>
                            </div>
                            <div class="p-2 border rounded-md bg-gray-50">
                                <span class="font-semibold text-gray-700">② 키워드 포함 (Max ${feedback.keyword.max.toFixed(1)}점):</span> 
                                <span class="text-gray-600">${feedback.keyword.score.toFixed(2)}점. ${feedback.keyword.reason}</span>
                                ${feedback.keyword.found.length > 0 ? `<div class="text-xs mt-1 text-green-700">✔️확인된 키워드: [${feedback.keyword.found.join(', ')}]</div>` : ''}
                            </div>
                            <div class="p-2 border rounded-md bg-gray-50">
                                <span class="font-semibold text-gray-700">③ 구조/가독성 (Max ${feedback.structure.max.toFixed(1)}점):</span> 
                                <span class="text-gray-600">${feedback.structure.score.toFixed(2)}점. ${feedback.structure.reason}</span>
                            </div>
                        </div>
                    </div>
                `;
                container.innerHTML += html;
            }
        }


        function calculateScore() {
            const quantitative = calculateQuantitativeScore();
            const { scores: individualScores, total: qualitative } = calculateQualitativeScores();
            
            const total = parseFloat((quantitative + qualitative).toFixed(2));

            document.getElementById('quantitativeScore').textContent = quantitative.toFixed(1);
            document.getElementById('qualitativeScore').textContent = qualitative.toFixed(2);
            document.getElementById('totalScore').textContent = total.toFixed(2); 
            
            document.getElementById('resultContainer').classList.remove('hidden');
            
            // 상세 피드백 렌더링
            renderDetailedFeedback(individualScores);

            // 시뮬레이션 메시지 생성
            const messageElement = document.getElementById('simulationMessage');
            messageElement.className = 'mt-4 p-4 rounded-md text-center font-medium';

            if (qualitative === 40) {
                messageElement.classList.add('bg-green-100', 'text-green-800');
                messageElement.innerHTML = `
                    <span class="text-xl font-extrabold">🎉 정성 평가 만점(40.00점) 달성! 🎉</span> <br>
                    정량 점수 ${quantitative.toFixed(1)}점과 합산하여 최종 총점 <span class="font-extrabold">${total.toFixed(2)}점</span>입니다. 이대로 서류 제출을 준비하세요!
                `;
            } else if (total >= 80) {
                messageElement.classList.add('bg-green-100', 'text-green-800');
                messageElement.innerHTML = `
                    <span class="text-xl font-extrabold">${total.toFixed(2)}점 달성!</span> <br>
                    매우 우수한 점수입니다. (90점 만점 기준) 1차 서류 전형 합격이 매우 유력합니다.
                `;
            } else if (total >= 70) {
                 messageElement.classList.add('bg-indigo-100', 'text-indigo-800');
                 messageElement.innerHTML = `
                    <span class="text-xl font-extrabold">${total.toFixed(2)}점입니다.</span> <br>
                    안정적인 점수대입니다. 상세 피드백을 확인하여 부족한 키워드와 가독성을 보완해 보세요.
                `;
            } else {
                 messageElement.classList.add('bg-red-100', 'text-red-800');
                 messageElement.innerHTML = `
                    <span class="text-xl font-extrabold">${total.toFixed(2)}점입니다.</span> <br>
                    합격권에 들기 위해서는 정성 평가 항목별 **상세 피드백**을 검토하여 내용을 대폭 보강해야 합니다.
                `;
            }

            // 스크롤 이동
            document.getElementById('detailedFeedbackContainer').scrollIntoView({ behavior: 'smooth' });
        }

        // 초기값 설정 및 화면 업데이트
        window.onload = function() {
            // 모든 텍스트 필드에 이벤트 리스너 추가
            for (const id in QUALITATIVE_FIELDS) {
                const textarea = document.getElementById(id);
                textarea.addEventListener('input', () => updateCharCount(id));
                updateCharCount(id); // 초기 상태 업데이트
            }
            
            // 정량 평가 셀렉트 박스나 체크박스 변경 시 점수 계산
            document.querySelectorAll('#majorStatus, #certificateCount, #careerPeriod, #awardRecord, #careerDiversity').forEach(element => {
                element.addEventListener('change', calculateScore);
            });

            // 초기 계산을 수행하여 0점 상태를 표시
            calculateScore(); 
        };
    </script>
</body>
</html>
