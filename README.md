# SRL VoiceBot

## Project info
### Dispatch Automation Platform
### 📌 Project Overview
The Dispatch Automation Platform is a scalable outbound call automation system built to manage and monitor driver communication workflows efficiently.
It enables operations teams to:

Upload driver data via CSV/XLSX

Automatically trigger AI-powered outbound calls

Track real-time call progress

Handle retry logic for unanswered calls

Capture transcripts and recordings

Maintain structured call history and analytics

The system is designed for reliability, controlled retries, and operational transparency.

🎯 Client Objective

The primary objective of this platform is to streamline operational communication between the control tower and drivers.

Key goals:

Ensure all drivers receive important updates

Reduce manual calling workload

Automatically retry unanswered calls

Maintain an auditable communication trail

Provide real-time visibility into call progress

Ensure high delivery completion rate

🏗 System Architecture

The system consists of:

1️⃣ Frontend Application

Batch upload (CSV/XLSX)

Dataset management

Live call status dashboard

Retry configuration controls

Realtime updates

2️⃣ Backend (Supabase Edge Functions)

Call dispatch orchestration

Webhook event processing

Retry scheduling

Dataset completion tracking

Call lifecycle management

3️⃣ Call Provider Integration

Outbound call triggering via API

Event-based webhook callbacks

Transcript and recording capture

🔄 Call Lifecycle

Each call follows a structured state machine:

Event	Resulting Status
Call triggered	ringing
Call initiated	active
Call completed	completed
No response within timeout	queued (retry scheduled)
Max retries exceeded	failed

Retries occur after a defined delay if no completion event is received.

📂 Data Flow

CSV/XLSX uploaded

Rows parsed into structured call records

Records inserted into database

Dispatcher claims next queued call

Call API triggered

Webhook updates status

Dataset auto-completes when all calls reach terminal state

🔁 Retry Logic

Configurable maximum attempts

Configurable retry delay

Backstop timeout protection for stuck calls

Idempotent status transitions

No duplicate dispatching

📊 Data Retention

The system maintains:

Call status history

Attempt count

Error messages

Transcripts

Recording URLs

Dataset summary metrics

Minimum retention: 30 days

🔐 Security Measures

Server-to-server webhook authentication

Edge function access control

Origin validation

Terminal state protection (no status override once completed/failed)

Controlled dataset-level concurrency

🚀 Deployment Environment

Supabase (Database + Edge Functions)

AI Call Provider API

Realtime subscriptions

Secure environment variable configuration

📈 Scalability

The platform supports:

Large batch uploads

Parallel dataset processing

Controlled sequential dispatch (if required)

Multi-attempt retry strategies

High observability via logs and real-time updates

🧪 Testing & Validation

The system has been validated for:

Successful call completion detection

Retry behavior on unanswered calls

Accurate dataset completion detection

Prevention of duplicate dispatch

Accurate transcript and recording storage

📞 Support & Maintenance

The platform includes:

Structured logging

Event-level debugging

Controlled retry behavior

Dataset-level analytics

Failure classification
